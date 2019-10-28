---
title: Windows Powershell / Planned Outage Command line access
summary: "Schedule planned outages from Windows Powershell / the command line."
sidebar: p_enterprise_sidebar
permalink: enterprise_cfgmonitor_plannedoutage_commandline.html
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

Basic commands

* List Spotlight connections
* Add a planned outage scheduled to occur once only
* Add a planned outage scheduled to occur every day
* Add a planned outage scheduled to occur on given days of the week
* Add a planned outage scheduled to occur on the given day of the given months
* Get help

Command parameters

Parameter | Use
----------|----
-Address | Required
-ReoccurenceType | Once, daily, weekly or monthly.
-StartTime | Used to add a planned outage scheduled to occur every day, on given days of the week or given days of given months.
-FinishTime | Used to add a planned outage scheduled to occur every day, on given days of the week or given days of given months.
-StartDateTime | Used to add a planned outage scheduled to occur once only.
-FinishDateTime | Used to add a planned outage scheduled to occur once only.
-Description | Optional. Use with any Add-Outage command
-DaysOfWeek | Used to add a planned outage scheduled to occur on given days of the week.
-Day | Used to add a planned outage scheduled to occur on the given day of the given months.
-WhichWeekInMonth | Used to add a planned outage scheduled to occur on the given day of the given months.
-MonthInterval | Used to add a planned outage scheduled to occur on the given day of the given months.

## Basic commands

### List Spotlight connections

```
Get-Connection
```

### Add a planned outage scheduled to occur once only

```
Add-Outage -Address @{SqlServer="sqlserver1,sqlserver2,sqlserver3"; Windows="windows1,windows2,windows3"} -ReoccurenceType Once -StartDateTime "10/27/2018 10:46" -FinishDateTime "10/27/2018 12:46" -Description OnceOutageDescription -PassThru
```


### Add a planned outage scheduled to occur every day

```
Add-Outage -Address @{SqlServer="sqlserver1,sqlserver2,sqlserver3"; Windows="windows1,windows2,windows3"} -ReoccurenceType Daily -StartTime "10:46" -FinishTime "12:46" -Description DailyOutageDescription -PassThru
```


### Add a planned outage scheduled to occur on given days of the week

```
Add-Outage -Address @{Replication="replication1,replication2"; VMware="vmware1,vmware2,vmware2"} -ReoccurenceType Weekly -DaysOfWeek Monday,Tuesday,Friday -StartTime "1:46" -FinishTime "2:46" -Description "WeeklyReplication and VMware" -PassThru
```


### Add a planned outage scheduled to occur on the given day of the given months

```
Add-Outage -Address @{SqlServer="sqlserver1,sqlserver2,sqlserver3"; Windows="windows1,windows2,windows3"} -ReoccurenceType Monthly -Day 2 -MonthInterval 3 -StartTime "10:46" -FinishTime "12:46" -Description MonthlyFixedOutageDescription -PassThru
```


```
Add-Outage -Address @{SqlServer="sqlserver1,sqlserver2,sqlserver3"; Windows="windows1,windows2,windows3"} -ReoccurenceType Monthly  -WhichWeekInMonth "second" -DayOfWeekInMonth "weekday" -MonthInterval 4 -StartTime "10:46" -FinishTime "12:46" -Description MonthlyNonFixedOutageDescription -PassThru
```


### Get help

```
Get-Help Add-Outage -full
```


## Windows Powershell / Command line parameters

### -Address address
List the connections to be added to the planned outage in the form @{SqlServer="sqlserver1"} where in this example *SqlServer* is the connection type and *sqlserver1* the address of the SQL Server connection.

The connection types are (case insensitive):

* sqlserver
* windows
* hyperv
* analysisservices
* availabilitygroup
* replication
* sqlazure
* vmware
* unix/linux

For multiple connections of the same connection type, separate each address with a comma as in @{SqlServer="sqlserver1,sqlserver2"}

For multiple connections of different connection types, list connections of each type separately as in @{SqlServer="sqlserver1,sqlserver2"; Windows="windows1,windows2"}

The address of the connection can take the same forms as available in the **Spotlight Client \| Configure Connections \| Properties \| Details \| Address field**. For example: the Server Name, Server Instance Name, or IP address.


{% include note.html content="The -Address command line parameter is required. It cannot be empty or null. If the address does not exist the command will fail." %}

{% include note.html content="The -Name command line parameter (used to [List / edit / delete Spotlight Connections][enterprise_connect_commandline]) is not available with the Add-Outage command." %}


### -ReoccurenceType value

Value | Description
------|------------
Once | This planned outage is scheduled to occur once only.
Daily | This planned outage is scheduled to occur every day.
Weekly | This planned outage is scheduled to occur on the given day(s) of the week.
Monthly | This planned outage is scheduled to occur on the given day(s) of the given months.

### -StartTime "12:46"
Used to add a planned outage scheduled to occur every day, on given days of the week or given days of given months. Enclose the time in double quotes. The start time of the planned outage is of the form: hh:mm


### -FinishTime "13:46"  
Used to add a planned outage scheduled to occur every day, on given days of the week or given days of given months. Enclose the time in double quotes. The finish time of the planned outage is of the form: hh:mm

{% include note.html content="The add-outage command will fail if the time format is wrong or time period is unreasonable, such as the -FinishTime is before the -StartTime." %}



### -StartDateTime "11/4/2018 12:46"
Used to add a planned outage scheduled to occur once only.

The start date and time of the planned outage is of the form: "mm/dd/yyyy hh:mm"

Enclose the date and time in double quotes.

The time is as per the time zone of the Spotlight Diagnostic Server.


### -FinishDateTime  "11/4/2018 13:46"
Used to add a planned outage scheduled to occur once only.

The end date and time of the planned outage of the form: "mm/dd/yyyy hh:mm"

Enclose the date and time in double quotes.

The time is as per the time zone of the Spotlight Diagnostic Server.

{% include note.html content="The add-outage command will fail if the time format is wrong or time period is unreasonable, such as the -FinishDateTime is before the -StartDateTime." %}



### -Description "description"
A description for the planned outage as will be displayed on the [Planned Outage dialog][enterprise_cfgmonitor_plannedoutage].


### -DaysOfWeek Monday,Tuesday,Friday
Used to add a planned outage scheduled to occur on given days of the week.

Add the days of the week to conduct the planned outage, separated by a comma.


### -Day 2
Used to add a planned outage scheduled to occur on the given day of the given months.

In the above example the outage is scheduled to occur on the second day of given months.

To schedule a planned outage for the last day of the month over multiple months select 31 as the day of the month. This will schedule the outage to the last day of the month regardless of whether the month has 31 days. If the selected day of the month is 29, 30 or 31 then for months that have fewer than those number of days the planned outage will be scheduled for the last day of the month.


### -WhichWeekInMonth "second" -DayOfWeekInMonth "weekday"
Used to add a planned outage scheduled to occur on the given day of the given months.

In the above example the outage is scheduled to occur in the second week of the month on a weekday.


### -MonthInterval 4
Used to add a planned outage scheduled to occur on the given day of the given months.

In the above example the outage is scheduled to occur every 4 months.


{% include links.html %}
