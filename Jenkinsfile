@Library("F1-PipelineLibraries") _
timestamps
{
    nodeWithProperWorkspace('VS2017ForSoSSE131', 'SE')
    {
        stage 'Prepare'
            bat "RD /S /Q . > nul || echo bypass error" 
    		bat 'md OnlineHelp | exit /b 0'
    		def CurrentDir=pwd()
        stage 'Checkout SpotlightHelp'
            dir("${CurrentDir}/OnlineHelp") {
				checkout scm
			}
        stage 'Build SpotlightHelp'
            dir("${CurrentDir}/OnlineHelp") {
                def buildhelp = load("_build/BuildHelp.groovy")
				buildhelp.BuildHelp()
            }
        stage 'Upload to Artifactory'
            def zip = '"C:\\Program Files\\7-Zip\\7z.exe"'
            dir("${CurrentDir}/OnlineHelp") { 
                bat """${zip} a ${CurrentDir}\\OnlineHelp\\OnlineHelp.zip ${CurrentDir}\\OnlineHelp\\_install"""
				bat """${zip} a ${CurrentDir}\\OnlineHelp\\OnlineHelp.zip ${CurrentDir}\\OnlineHelp\\_site"""
				bat """${zip} a ${CurrentDir}\\OnlineHelp\\OnlineHelp.zip ${CurrentDir}\\OnlineHelp\\_siteBalloonHelp"""
				
				def uploadPattern = "OnlineHelp.zip"
				def targetPath = "Spotlight-Enterprise-libs/SpotlightHelp/${env.BRANCH_NAME}/OnlineHelp.zip"
				UploadToArtifactory(uploadPattern, targetPath)
            }
    }
}

void nodeWithProperWorkspace(def slave, def space, def body) {
    node (slave) {
        ws(space) {
            body.call()
        }
    }
}
