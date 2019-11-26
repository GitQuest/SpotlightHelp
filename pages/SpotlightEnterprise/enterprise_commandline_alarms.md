---
title: Windows Powershell / Alarms Command line 
summary: "Get / Acknowledge / Snooze Alarms from Windows Powershell / the command line."
sidebar: p_enterprise_sidebar
permalink: enterprise_commandline_alarms.html
folder: SpotlightEnterprise
---


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

{% include links.html %}