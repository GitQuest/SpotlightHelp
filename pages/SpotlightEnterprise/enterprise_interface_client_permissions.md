---
title: Permission to use Spotlight
summary: "The Spotlight Client is granted permission to run Spotlight, acknowledge, snooze and ignore alarms, configure Spotlight and execute tasks on monitored Windows Server and SQL Server according to the membership of the Windows credentials used to run the Spotlight Client. Spotlight uses membership of the Spotlight diagnostic user groups, Windows groups created on install of Spotlight, to authenticate Spotlight Client access to the Spotlight Diagnostic Server. The Windows credentials used to run the Spotlight Client must be a member of at least one of the three groups: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required."
sidebar: p_enterprise_sidebar
permalink: enterprise_interface_client_permissions.html
folder: SpotlightEnterprise
---


## Permission to use Spotlight

The Windows credentials used to run the Spotlight Client must be a member of at least one of the three groups for the given Spotlight Diagnostic Server: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required. These groups exist locally on the Spotlight Diagnostic server host; members can be added and removed through Computer Management > Local Users and Groups.

## Acknowledge, snooze and ignore alarms

The Windows credentials used to run the Spotlight Client grant required permissions for the Spotlight Client to acknowledge, snooze and ignore alarms. There are three Windows groups: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required.

Icon | Action | Administrator | User | Read-only
-----|--------|---------------|------|----------
{% include inline_imageClient.html file="tb_alarms_acknowledge.png" alt="Acknowledge" %} | Acknowledge | Yes | Yes | No
{% include inline_imageClient.html file="tb_action_snooze.png" alt="Snooze" %} | Snooze Alarm | Yes | Yes | No
{% include inline_imageClient.html file="tb_action_ignorealarm.png" alt="Ignore" %} | Ignore Alarm | Yes | Yes | No


## Configure Monitoring

The Windows credentials used to run the Spotlight Client grant required permissions for the Spotlight Client to configure the Spotlight Diagnostic Server. There are three Windows groups: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required.

Icon | Action | Administrator | User | Read-only
-----|--------|---------------|------|----------
{% include inline_imageClient.html file="tb_config_connections.png" alt="Configure Connections" %} | Configure Connections: Add/Delete connection profiles | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_connections.png" alt="Configure Connections" %} | Configure Connections: Add/Replace/Delete tags | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_connections.png" alt="Configure Connections" %} | Configure Connections: Enable/Disable monitoring | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_alarms.png" alt="Configure Alarms" %} | Configure Alarms | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_alarmactions.png" alt="Alarm Action Editor" %} | Alarm Action Editor | Yes | No | No
{% include inline_imageClient.html file="tb_config_scheduling.png" alt="Configure Scheduling" %} | Configure Scheduling | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_plannedoutage.png" alt="Configure Planned Outage" %} | Configure Planned Outage (Add, Edit, Remove) | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_sqlserverresponse.png" alt="Configure SQL Server Response Time" %} | Configure SQL Server Response Time | Yes | No | No
{% include inline_imageClient.html file="tb_config_customcounters.png" alt="Configure Custom Counters" %} | Configure Custom Counters | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_errorlogentries.png" alt="Configure Error Log Entries" %} | Configure Error Log Entries | Yes | No | No
{% include inline_imageClient.html file="tb_config_monitoredfiles.png" alt="Configure Monitored Files" %} | Configure Monitored Files | Yes | Yes | No
 | Apply Configuration To… | Yes | Yes | No
 | Configuration templates (Save, Delete, Rename) | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_defragmentation.png" alt="Configure Defragmentation Collection" %} | Configure Defragmentation Collection | Yes | Yes | No


## Configure the Diagnostic Server

The Windows credentials used to run the Spotlight Client grant required permissions for the Spotlight Client to configure the Spotlight Diagnostic Server. There are three Windows groups: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required.

Icon | Action | Administrator | User | Read-only
-----|--------|---------------|------|----------
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Select a Diagnostic Server | Yes | Yes | Yes
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure the database maintenance schedule | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure PagerDuty | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure the Diagnostic Server's mail server | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure the Playback Database | Yes | Yes | No
 | Configure Store SQL text and query plans in playback | Yes | No | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure the SNMP Trap | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure the Spotlight Statistics Repository | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Configure the use of Extended Events | Yes | No | No
{% include inline_imageClient.html file="tb_config_spotlightcloud.png" alt="Configure Spotlight Cloud" %} | Configure uploading to Spotlight Cloud | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Federate Diagnostic Servers | Yes | Yes | No
{% include inline_imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %} | Manage access to Spotlight connections | Yes | No | No

## Configure the Spotlight Client

Icon | Action | Administrator | User | Read-only
-----|--------|---------------|------|----------
{% include inline_imageClient.html file="tb_config_spotlight.png" alt="Configure Spotlight" %} | Change Display  | Yes | Yes | Yes
{% include inline_imageClient.html file="tb_config_spotlight.png" alt="Configure Spotlight" %} | Troubleshoot Spotlight  | Yes | Yes | Yes
{% include inline_imageClient.html file="tb_config_userexperience.png" alt="Configure User Experience" %} | User Experience | Yes | Yes | Yes


## Execute tasks on monitored SQL Server

The Windows credentials used to run the Spotlight Client grant required permissions for the Spotlight Client to execute actions on monitored SQL Server. There are three Windows groups: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required.

Drilldown icon | SQL Server drilldowns | Administrator | User | Read-only
---------------|-----------------------|---------------|------|----------
{% include inline_imageClient.html file="tb_drilldown_sqlactivity.png" alt="SQL Activity" %} | SQL Activity \| Sessions \| Kill Session | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_databases.png" alt="Databases" %} | Databases \| Indexes \| Update Statistics | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_support.png" alt="Support Services" %} | Support Services \| SQL Agent Jobs \|  Start Job | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_support.png" alt="Support Services" %} | Service Status \| Start / Stop Service | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_support.png" alt="Support Services" %} | Cluster Services \| Take Offline | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_support.png" alt="Support Services" %} | Cluster Services \| Bring Online | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_support.png" alt="Support Services" %} | Cluster Services \| Move Group | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_config.png" alt="Configuration" %} | Configuration \| Change parameter | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_errorlog.png" alt="Error Log" %} | Error Log \| Cycle Error log | Yes | No | No


## Execute tasks on monitored Windows Server

The Windows credentials used to run the Spotlight Client grant required permissions for the Spotlight Client to execute actions on monitored Windows server. There are three Windows groups: Spotlight Diagnostic Administrators, Spotlight Diagnostic Users, Spotlight Diagnostic Read-Only. Your Network Administrator can add members, increase and decrease your membership as required.

Drilldown icon | Windows Server drilldowns | Administrator | User | Read-only
---------------|---------------------------|---------------|------|----------
{% include inline_imageClient.html file="tb_drilldown_process.png" alt="Processes" %} | Processes \| Terminate | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_process.png" alt="Processes" %} | Services \| Start | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_process.png" alt="Processes" %} | Services \| Stop | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_process.png" alt="Processes" %} | Services \| Pause | Yes | No | No
{% include inline_imageClient.html file="tb_drilldown_process.png" alt="Processes" %} | Services \| Resume | Yes | No | No


{% include links.html %}
