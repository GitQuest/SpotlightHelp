BUILD_RTM_DEFAULT=false
BUILD_CONFIG_DEFAULT='Release'
JRE_VERSION_DEFAULT='1.8.0_102'

properties([[$class: 'ParametersDefinitionProperty',
    parameterDefinitions: [
        [$class: 'BooleanParameterDefinition',
         defaultValue: BUILD_RTM_DEFAULT,
         description: 'If checked, downgrading will be disabled',
         name: 'BUILD_RTM'
        ],
        [$class: 'ChoiceParameterDefinition',
         choices: "${BUILD_CONFIG_DEFAULT}\nDebug",
         description: 'The Visual Studio build solution configuration to use',
         name: 'BUILD_CONFIG'
        ],
        [$class: 'StringParameterDefinition',
         defaultValue: JRE_VERSION_DEFAULT,
         description: 'The JRE version to be distributed',
         name: 'JRE_VERSION'
        ]
    ]
]])

RTMBuild = "${binding.hasVariable('BUILD_RTM') ? BUILD_RTM : BUILD_RTM_DEFAULT}"
VSBuildConfiguration = "${binding.hasVariable('BUILD_CONFIG') ? BUILD_CONFIG : BUILD_CONFIG_DEFAULT}"
JREVersion = "${binding.hasVariable('JRE_VERSION') ? JRE_VERSION : JRE_VERSION_DEFAULT}"

timestamps
{
    nodeWithProperWorkspace('slavetemplate', 'SE')
    {
        stage 'Preparation'
        bat 'powershell -NoProfile -Command "Get-Process | where {$_.MainModule.FileName -like \'%cd%*\'} | Stop-Process -Force -PassThru" | exit /b 0'
        bat 'md DiagnosticServer | exit /b 0'
        bat 'md Spotlight | exit /b 0'
        bat 'md OnlineHelp | exit /b 0'
        def CurrentDir=pwd()

        echo "Is RTM build?: ${RTMBuild}"
        echo "Visual Studio build configuration: ${VSBuildConfiguration}"
        echo "Distributing JRE version ${JREVersion}"

        stage 'Checkout Help'
        dir("${CurrentDir}/OnlineHelp")
        {
            deleteDir()
            checkout scm
        }

        def PARENTBRANCH=readFile(encoding: 'UTF-8', file: "${CurrentDir}/OnlineHelp/build/parentbranch.txt").trim()
        def DSBRANCH
        def CLIENTBRANCH

        stage 'Checkout DS'
        dir("${CurrentDir}/DiagnosticServer")
        {
            DSBRANCH = checkoutBranchWithParent('DiagnosticServer', PARENTBRANCH)
        }
        
        stage 'Checkout Client'
        dir("${CurrentDir}/Spotlight")
        {
            CLIENTBRANCH = checkoutBranchWithParent('Spotlight', PARENTBRANCH)
        }

        dir("${CurrentDir}/DiagnosticServer")
        {
            def ds = load("${CurrentDir}/DiagnosticServer/build/BuildDS.groovy")
            ds.BuildDS(env.BRANCH_NAME, DSBRANCH, CLIENTBRANCH, PARENTBRANCH)
        }

        dir("${CurrentDir}/OnlineHelp")
        {
            def buildhelp = load("${CurrentDir}/OnlineHelp/build/BuildHelp.groovy")
            buildhelp.BuildHelp()
        }
        
        dir("${CurrentDir}/Spotlight")
        {
            def client = load("${CurrentDir}/Spotlight/build/BuildClient.groovy")
            client.BuildClient(env.BRANCH_NAME, DSBRANCH, CLIENTBRANCH, PARENTBRANCH)
        }

        dir("${CurrentDir}/DiagnosticServer")
        {
            def dstest = load("${CurrentDir}/DiagnosticServer/build/TestDS.groovy")
            dstest.TestDS()
        }

        dir("${CurrentDir}/Spotlight")
        {
            def clienttest = load("${CurrentDir}/Spotlight/build/TestClient.groovy")
            clienttest.TestClient()
        }
    }

    nodeWithProperWorkspace('qatemplate', 'QA')
    {
        def PARENTBRANCH='master' // TODO This needs to be changed for each release
        def CurrentDir=pwd()
        def gitTool = tool name: 'Default', type: 'hudson.plugins.git.GitTool'

        // Support long names
        bat """"${gitTool}" config --system core.longpaths true"""

        stage 'Checkout Automation Test'
        checkoutBranchWithParent('Spotlight-Azure-Autotesting', PARENTBRANCH)

        def test
        test = load("${CurrentDir}/build/SmokeTest.groovy")
        // TODO We should pass the complete build number, e.g. 12.0.0.123
        test.SmokeTest(env.BRANCH_NAME, env.BUILD_NUMBER)
    }
}

void nodeWithProperWorkspace(def slave, def space, def body) {
    node (slave) {
        ws(space) {
            body.call()
        }
    }
}

def checkoutBranch(def repo, def branch)
{
    checkout([$class: 'GitSCM',
              branches: [[name: "origin/${branch}"]],
              doGenerateSubmoduleConfigurations: false,
              submoduleCfg: [],
              userRemoteConfigs: [[url: "git@github.com:GitQuest/${repo}.git",
                                   credentialsId: '183428da-830f-4cc3-a535-6979620b1d52']],
              extensions: [[$class: 'PruneStaleBranch'], [$class: 'CleanBeforeCheckout']]
             ]
    )
}

def checkoutBranchWithParent(def repo, def parent)
{
    // [name: "origin/${parent}"] TODO: fix alternative build plugin
    // using https://issues.jenkins-ci.org/browse/JENKINS-37136 for tracking
    try
    {
        checkoutBranch(repo, env.BRANCH_NAME)
        return env.BRANCH_NAME
    }
    catch(all)
    {
        echo "Defaulting to parentbranch $parent as branch ${env.BRANCH_NAME} is not available"
        checkoutBranch(repo, parent)
        return parent
    }
}
