---
title: Log of user actions
summary: "Spotlight maintains an audit log of user actions. This log is a historical record of who changed what configuration when."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_logofuseractions.html
folder: SpotlightEnterprise
---


## How to generate the log and access the information

From the Spotlight Client

1. Click **Reports** to show the reports that are available from this Spotlight Client.
3. From **Default Reports**, select **Audit Report**.
3. You may be required to provide authentication to the Spotlight Playback Database. Data for the log is stored in the Spotlight Playback Database.
4. Fill in the input parameters.
5. Click **View Report**.

For general information on Spotlight Reports, see [Spotlight Reports][enterprise_display_reports].


## Data source of the log

Data for the log is stored in the [Spotlight Playback Database][enterprise_backend_playback].

## Record Details

For the following user actions the log records:

* The Spotlight user making the change.
* The time the change was made.
* The configuration that was changed (if applicable).
* The configuration value before and after the change (if applicable).

The log also records startup and shutdown of Spotlight Clients.

## Changes to Configure \| Spotlight

### Connections

Manage the connections monitored by Spotlight. The log records all applied changes.

### Alarms

Set the thresholds and severities that determine when an alarm is raised. The log records all changes as applied to a monitored connection or template.

### Alarm Actions

Set actions for Spotlight to take when an alarm is raised. The log records all saved changes.

### Scheduling

Spotlight collects data according to set schedules. The log records all changes to these schedules as applied to a monitored connection or template.

### Planned Outage

Changes to Planned Outage are recorded in the log of user actions.

### SQL Server Response Time

The log records changes to the SQL statement used to measure SQL Server response time as applied to a monitored connection or template.

### Custom Counters

The log records changes to the configuration of custom counters as applied to a monitored connection or template.

### Error Log Entries

The log records changes to the error log entries Spotlight is configured to scan the SQL Server error log for, as applied to a monitored connection or template.

### Monitored Files

The log records changes to the list of files tracked for size by Spotlight as applied to a monitored connection or template.

### Spotlight

Changes to the configuration of the Spotlight Client are not recorded in the log of user actions. The Spotlight Client is configured by changes to:

* Configure \| Spotlight \| Change Display
* Configure \| Spotlight \| Troubleshoot Spotlight

### Diagnostic Server

The log does not record

* changes to the Spotlight Client connected to the Spotlight Diagnostic Server.
* changes made to the Select a Diagnostic Server dialog.

The log does record changes to the configuration of the Diagnostic Server:

* Configure PagerDuty
* Configure the Diagnostic Server's mail server
* Configure the Playback Database
* Configure the SNMP Trap
* Configure the Spotlight Statistics Repository
* Configure the use of Extended Events
* Federate Diagnostic Servers


### Spotlight Cloud

The log records changes to the configuration - upload data to the Spotlight Cloud.

### User Experience


Changes to User Experience are not recorded in the log of user actions.

### Configuration Templates

Changes to Configuration Templates (Save, Delete, Rename) are recorded in the log of user actions.


## Changes to the Spotlight License

### Help \| About \| Product license

Changes to the product license are recorded in the log of user actions.


## When an alarm is acknowledged, snoozed or ignored

### Acknowledge

The log records when an alarm is acknowledged.

### Snooze Alarm

The log records when an alarm is snoozed.

### Ignore Alarm

The log records when an alarm is ignored.


## Changes to monitored SQL Server

### SQL Activity drilldown

The log records when a user kills a session from the Spotlight Client. That is command **Sessions \| Kill Session**.

{% include imageClient.html file="tb_drilldown_session_kill.png" alt="Kill Session" %}

### Databases drilldown

The log records when a user runs the Update Statistics command on selected indexes from the Spotlight Client. This command is run from the Indexes page of the Databases drilldown.

### Support Services drilldown

The log records when a user starts a SQL agent job from the Spotlight Client. That is command **SQL Agent Jobs \| Start Job**.

{% include imageClient.html file="tb_action_startjob.png" alt="Start Job" %}

The log records when a user changes the running state (Start / Stop) of a service from the Spotlight Client. This change is actioned from the Service Status page of the Support services drilldown.

The log records when a user takes the following actions on Cluster Services from the Spotlight Client:
* Take Offline - Makes a cluster resource or cluster group unavailable.
* Bring Online - Starts a cluster resource or group.
* Move Group - Moves a cluster group to another node of the cluster.


### Configuration drilldown

The log records when a user changes a configuration parameter from the Spotlight Client.

### Error Log drilldown

The log records when a user archives the current error log file and opens a new log file from the Spotlight Client. That is command **Cycle Error log**.

{% include imageClient.html file="tb_drilldown_errorlog_cycle.png" alt="Cycle Error log" %}


## Changes to monitored Windows Server

### Windows Server | Processes drilldown

The log records when a user:

* Terminates a process from the Spotlight Client.
* Changes the running state (start, stop, pause, resume) of a service or device from the Spotlight Client.



{% include links.html %}
