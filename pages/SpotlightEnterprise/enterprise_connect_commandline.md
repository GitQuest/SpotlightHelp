---
title: Windows Powershell / Command line access
summary: "List / edit / delete Spotlight Connections from Windows Powershell / the command line."
sidebar: p_enterprise_sidebar
permalink: enterprise_connect_commandline.html
folder: SpotlightEnterprise
---


## Requirements
Microsoft Windows Powershell 3.0 or above is required. Older operating systems (for example Windows Server 2008 R2) require an upgrade of the Windows Management Framework in order to access Spotlight from the command line. [Download Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595)

For commands where user / password details are required ensure the user is a member of the [Spotlight Diagnostic User Groups](enterprise_backend_spotlightdiagnosticusergroups) **Spotlight Diagnostic Administrators** or **Spotlight Diagnostic Users**. Where there are multiple Spotlight Diagnostic Servers in a [federation](enterprise_backend_federation) the user is required to be a member of Spotlight Diagnostic Administrators or Spotlight Diagnostic Users for all Spotlight Diagnostic Servers in the federation.

## 1. Access Spotlight from Windows Powershell / the command line

From Windows Powershell, enter command: **Import-DS | Add-DS -PassThru**.

{% include tip.html content="Enter command **get-dS** to verify the Spotlight Diagnostic Server has been imported correctly." %}

{% include tip.html content="In some special situations or for some platforms, if **Import-DS** does not work for you then open the **Console** directory in the Spotlight Client installation directory (usually C:\Program Files (x86)\Quest Software\Spotlight Enterprise). Right click the file **ds-cli.cmd** and select **Open** to open the command prompt." %}


## 2. Command Spotlight from Windows Powershell / the command line

* Basic commands
* Windows Powershell / Command line parameters
* Add a list of connections
* Remove many connections
* Alarm commands
* Manage access to Spotlight connections

## Basic commands

### List Spotlight connections

```
Get-Connection
```


### Delete a Spotlight connection

See also [Remove many connections](#RemoveManyConnections).

```
Remove-Connection -Name connectionName -PassThru
```



### Add a Spotlight connection

#### Windows authentication (using Diagnostic Server credentials)

See also [Add a list of connections](#AddAListOfConnections).

```
Add-Connection -Address address -Technology connectionType -Tag tag -Enabled -PassThru
```

#### Supply User / Password details

See also [Add a list of connections](#AddAListOfConnections).

```
Add-Connection -Credential $(get-credential) -Address address -Technology connectionType -Tag tag -Enabled -PassThru
```



### Change the authentication used to monitor a Spotlight connection

#### Supply User / Password details

```
Get-Connection -Name connectionName | Set-Connection -Credential $(get-credential)
```

#### Change to Windows authentication (using Diagnostic Server credentials)

```
Get-Connection -Name connectionName | Set-Connection -UseDSAuth
```

#### Update Tag (using Diagnostic Server credentials)

```
Get-Connection -Name connectionName | Set-Connection -Tag tag
```

### Disable monitoring a Spotlight connection

```
Get-Connection -Name connectionName | Set-Connection -Disabled
```

### Re-enable monitoring a Spotlight connection

```
Get-Connection -Name connectionName | Set-Connection -Enabled
```

## Windows Powershell / Command line parameters

### -Name connectionName

Supply the name of the connection.

{% include note.html content="The connection name is not user-assignable. When executing Add-Connection from the command line, the connection name will take the form of the address followed by the connection type, as in address_connectionType" %}

Connection names are not case sensitive.

{% include tip.html content="A list of connection names can be summarized by wildcards * and ? as per prefix* or \*infix\* or on?char." %}

### -Address address

Supply the address of the Spotlight connection as per the form of the address entered in the **Spotlight Client \| Configure Connections \| Properties \| Details \| Address field**. For example: the Server Name, Server Instance Name, or IP address.

### -Technology connectionType

Supply the connection type in Internet MIME format. For example: os/windows, os/vmware. More free form forms are accepted such as windows, vmware, hyperv, sqlserver, sqlazure, analysisservices, replication and availabilitygroups.

### -Tag tag

Supply the tag of the connection, not case sensitive, input one of tags or all of the tags, no need input the # sign.

### -Credential $(get-credential)

Use the -Credential parameter to specify User / Password details as per the connection type. For Add-Connection, where the -Credential parameter is not specified, Windows authentication (using Diagnostic Server credentials) is assumed.

The -Credential parameter requires a PSCredential object, which is a Powershell built-in object.

It can be used via a temporary variable (preferable if you want to add many connections) as per:

```
$c = $(get-credential)

Add-Connection -Credential $c -Technology sqlserver -Address my.host.name\instance -Enable
```

It can be used inline as per:

```
Add-Connection -Credential $(get-credential) -Technology sqlserver -Address my.host.name\instance -Enable
```

### -Enabled

Enable Spotlight monitoring on this connection.


### -Disabled


Disable Spotlight monitoring on this connection.


## Add a list of connections {#AddAListOfConnections}

Add a list of connections where all connections are of the same technology / connection type. Separate each address with a comma. Supply one technology type.

```
Add-Connection -Address address1,address2,address3 -Technology connectionType -Tag tag -Enabled -PassThru
```

Add a list of connections where there are varying connection types. Separate each address with a comma. Provide a list of technology types where the first address corresponds to the first technology type, the second address corresponds to the second technology type etc.

```
Add-Connection -Address address1,address2,address3 -Technology connectionType1,connectionType2,connectionType3 -Enabled -PassThru
```


## Remove many connections {#RemoveManyConnections}

Remove all connections

```
Remove-Connection -Name *
```


Remove all connections of a specific type (technology)

```
Remove-Connection -Technology connectionType
```

For example to remove all connections where the connection type is SQL Server:

```
Remove-Connection -Technology sqlserver
```

Remove a list of connections. Type the name of each connection. Separate each connection name with a comma.

```
Remove-Connection -Name connectionName1,connectionName2,connectionName3
```

Remove a list of connections where the connection names form a pattern.

```
Remove-Connection -Name connectionName*
```

For example to remove all connections where the name begins with the characters "address":

```
Remove-Connection -Name address*
```

## Alarm commands

### Get alarms

Fetch alarms from Diagnostic Server

Command parameters

Parameter | Use
----------|----
-Technology | Required, SQL Server, Windows, Unix/Linux, Diagnostic Server etc.
-ConnectionDisplayName | Connection display name, case insensitive.
-FirstRaisedTime | Alarm first raised earlier than this time.
-LastRaisedTime | Alarm last raised earlier than this time.
-AlarmName | Alarm display name,case insensitive.
-Snoozed | $True or $False.
-Severity | Low, Medium, High, Information, Normal, Disabled.

Get alarms by connection display name

```
Get-Alarms -Technology windows,sqlserver -ConnectionDisplayName @("sqlserver2016", "zhuhaihosts")
```

Get alarms by LastRaisedTime and severity

```
$lastRaised = Get-Date -Date "2018-12-12 16:30:45"
Get-Alarms -Technology sqlserver -LastRaisedTime $lastRaised -Severity @("High", "Low")
```

### Acknowledge alarms

Acknowledge alarms from Get-Alarm output

```
Get-Alarms -ConnectionName @("connection1") -Technology sqlserver -Severity @("Low") | Update-AckAlarm -Message "Ack by DBA"
```

Acknowledge alarms in one or more requests

```
$ackAlarmRequest = New-Object DiagnosticServer.Install.Utilities.ObjectModel.AlarmQueue.AckAlarmRequest
$ackAlarmRequest.DiagnosticServerHost = "Hostname:3843"
$snoozeAlarmRequest.MonitoredEntityName = "sosseazuredb_sqlazure"
$ackAlarmRequest.Message = "Ack from powershell"

$ackAlarmRequest1 = New-Object DiagnosticServer.Install.Utilities.ObjectModel.AlarmQueue.AckAlarmRequest
$ackAlarmRequest1.DiagnosticServerHost = "Hostname1:3843"
$snoozeAlarmRequest1.MonitoredEntityName = "sosseazuredb1_sqlazure"
$ackAlarmRequest1.Message = "Ack from powershell"

$ackAlarmRequests = @($ackAlarmRequest,$ackAlarmRequest1)
Update-AckAlarms -Alarms $ackAlarmRequests
```

### Snooze alarms

Snooze alarms from Get-Alarm output

```
$snoozedUntilDate = Get-Date -Date "2020-12-31 12:00:00"
Get-Alarms -Technology windows -Severity @('information')| Update-SnoozeAlarm -SnoozeUntilDate $snoozedUntilDate
```

Snooze alarms in one or more requests

```
$snoozeAlarmRequest = New-Object DiagnosticServer.Install.Utilities.ObjectModel.AlarmQueue.SnoozeAlarmRequest
$snoozeAlarmRequest.DiagnosticServerHost = "DSGJL9Y2W1:3843"
$snoozeAlarmRequest.MonitoredEntityName = "sosseazuredb_sqlazure"
$snoozeAlarmRequest.SnoozeUntilDate = Get-Date -Date "2019-5-31 12:00:00"
$snoozeAlarmRequests = @($snoozeAlarmRequest)
Update-SnoozeAlarms $snoozeAlarmRequests
```

## Manage access to Spotlight connections commands

### Get-Users

Fetch users from "Spotlight Diagnostic Administrators", "Spotlight Diagnostic Users" and "Spotlight Diagnostic Read-Only Users" groups.

Command parameters

Parameter | Use
----------|----
-DS | DS address, case insensitive.
-User | User Name, Separate each user with a comma, fuzzy matching and case insensitive.
-Role | Role Name, Separate each Role with a comma, fuzzy matching and case insensitive..


Get all users or specific user

```
Get-Users
```

```
Get-Users -DS f1-w10-tvm01.melquest.dev.mel.au.qsft -Role ADMIN -User user
```

### Get-Permission

Get allowed or denied connections from DS(s), by default not show admin users.

Command parameters

Parameter | Use
----------|----
-DS | DS address, case insensitive.
-User | User Name, Separate each user with a comma, fuzzy matching and case insensitive.
-DisplayName | Connection display name, separate each display name with a comma, fuzzy matching and case insensitive.
-Technology | Technology name, separate each technology name with a comma, case insensitive.
-Tag | Connection Tag name, separate each Tag with a comma, when one tag it is fuzzy matching and when multiple tags it is full match, case insensitive.
-Denied | Display only the denied connections for the user(s).


```
Get-Permission -DS dsserver1.contoso.com -User contoso\user1 -DisplayName sqlserver1 -Technology sqlserver -Tag prod
```

```
Get-Permission -User contoso\user1,user2 -DisplayName sqlserver1,winserver1 -Tag prod,NewYork -Denied
```

### Grant-Permission

Grant user access permission to connection(s).

Command parameters

Parameter | Use
----------|----
-DS | DS address, case-insensitive.
-User | User Name, separate each user with a comma, fuzzy matching and case insensitive.
-ConnectionName | Connection technology name, separate each name with a comma, case insensitive.


Grant multiple connection permission to one user

```
Grant-Permission -User contoso\user1 -ConnectionName sqlserver1_replication,sqlserver1_sqlserver
```

Grant permission from Get-Permission command

```
Get-Permission -User contoso\user1,user2 -Denied -Techonlogy sqlserver | Grant-Permission
```


### Revoke-Permission

Revoke the user access permission from connection(s).

Command parameters

Parameter | Use
----------|----
-DS | DS address, case insensitive.
-User | User Name, separate each user with a comma, fuzzy matching and case insensitive.
-ConnectionName | Connection technology name, separate each name with a comma, case insensitive.


Revoke multiple connection permission to one user

```
Revoke-Permission -User contoso\user1 -ConnectionName winserver1,sqlserver1_sqlserver
```

Revoke permission from Get-Permission command

```
Get-Permission -User contoso\user1,user2 -ConnectionName winserver1,sqlserver1_sqlserver | Revoke-Permission
```

{% include links.html %}
