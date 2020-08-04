---
title: Upgrade Spotlight Enterprise
summary: "Upgrade Spotlight Enterprise using the Spotlight Enterprise installer."
sidebar: p_enterprise_sidebar
permalink: enterprise_upgrade.html
folder: SpotlightEnterprise
---



## Backup first
[Backup all Spotlight configuration and saved collection data][enterprise_backend_backupdata].

## Run the Spotlight Enterprise executable on each Spotlight Client
If your enterprise has multiple Spotlight Clients then ensure all Spotlight Clients are included in the upgrade process. If the Spotlight Client and Spotlight Diagnostic Server are running different versions of Spotlight Enterprise, the client will be unable to connect to the Spotlight Diagnostic Server.

If Spotlight Enterprise is deployed as a federated system of multiple Spotlight Diagnostic Server then make sure all the Spotlight Diagnostic Server in the federation are included in the upgrade process. For best practices, refer to [Upgrade Spotlight in a Federated Spotlight Deployment][enterprise_backend_federation_upgrade].

## Upgrade the Playback Database and Spotlight Statistics Repository
Following upgrade of the Spotlight Diagnostic Server, the Playback Database and Spotlight Statistics Repository are automatically upgraded the next time they are accessed by the Spotlight Diagnostic Server.

{% include note.html content="If in your environment the Playback Database / Spotlight Statistics Repository are replicated as per a Microsoft Replication database the upgrade can fail if schema changes are required that can only be made when replication is turned off. To successfully upgrade, the steps are to: turn replication off, upgrade the Spotlight Diagnostic Server, then re-enable replication." %}

## Frequently Asked Questions

### What configuration information is preserved on upgrade?
The following information on the Spotlight Diagnostic Server is preserved when you upgrade:

*  Connection properties for all monitored servers (including changes to scheduling and alarms)
*  Collection properties
*  Alarm Actions (These include running a program and sending an email.)
*  Planned Outages
*  Global options such as user-created Error Log rules
*  Configuration information for the Spotlight Statistics Repository (this applies only if you installed the Spotlight Statistics Repository from Spotlight on SQL Server) and the Playback Database.

### Which versions of Spotlight can I upgrade from?

Upgrade to Spotlight Enterprise from Spotlight on SQL Server 10.0 or above.

To upgrade from an earlier version of Spotlight on SQL Server than 10.0, upgrade to at least version 10.0 first.

To upgrade from Spotlight on SQL Server 10.5.0, first upgrade to 10.5.2 and then upgrade to Spotlight Enterprise.

### Spotlight Enterprise 13.2 and Internet Access
On upgrade to Spotlight Enterprise 13.2, If Windows Firewall is set up to block traffic by default then in Windows Firewall | Advanced Settings add new inbound and outbound rules to enable the following URLs on TCP port 443:
https://versions.spotlightcloud.io/

### Spotlight Enterprise 12.3 and SQL Server Error Log Alarms
On upgrade to Spotlight Enterprise 12.3 from 12.2 any Error Log alarms configured by you in the Spotlight Client, Configure \| Alarms dialog to be enabled, require acknowledgement, have changed content or ignore certain values, will have these configurations returned to Factory Settings. The Error Log Alarms have been refined and enhanced and are now fully configurable from the Spotlight Client, Configure | Error Log Entries dialog.

### Spotlight Enterprise 12.1 and SQL Server Waits
On upgrade to Spotlight Enterprise 12.1 there are new categories of wait events on the SQL Server Performance Health drilldown, Wait Statisitcs drilldown and Wait Events drilldown.

Categories of wait prior to 12.1 | Categories of wait 12.1 and above
---------------------------------|------------------------------------------
Wait (AlwaysOn)<br>Wait (Backup)<br>Wait (CLR)<br>Wait (DBM)<br>Wait (DTC)<br>Wait (IO)<br>Wait (Latch)<br>Wait (Lock)<br>Wait (Memory)<br>Wait (MISC)<br>Wait (Network)<br>Wait (Preemptive)<br>Wait (ServiceBroker)<br>Wait (SOS) | Wait (Idle)<br>Wait (Other)<br>Wait (Log)<br>Wait (CLR)<br>Wait (IO)<br>Wait (Network)<br>Wait (Memory)<br>Wait (Latch)<br>Wait (Remote Provider)<br>Wait (CPU)<br>Wait (Look)<br>Wait (XTP)

On Playback of data to the previous Spotlight Enterprise version:

Drilldown | Playback to the preious version
----------|---------------------------------
Wait Events | Data is displayed under categories of wait 12.1 and above
Performance Health | The Instance Wait Time chart shows the data
Wait Statistics | The Wait Time Trend chart shows no data. Waits Detail shows the data as collected under the categories of wait prior to 12.1


### Spotlight Enterprise 12.0.1 and SQL Server Connections \| 'Obscure string literals in SQL text and parameter’
On upgrade to Spotlight Enterprise 12.0.1 the value of the SQL Server connection property 'Obscure string literals in SQL text and parameters in query plans' will change to 'not selected' for all SQL Server.

Following upgrade you can select 'Obscure string literals in SQL text and parameters in query plans' for each SQL Server connection as required. From the Spotlight Client, Click **Configure \| Connections**, select the SQL Server connection and fill in the connection details.


### Exclude Spotlight sessions from Wait Events and Workload Analysis

When selected Spotlight sessions are excluded from the Wait Events and Workload Analysis drilldowns.

{% include note.html content="For monitored SQL Server versions earlier than SQL Server 2012 some long term Spotlight sessions may remain. For monitored SQL Server 2012 and above all Spotlight Sessions are excluded." %}

### File paths on upgrade from Spotlight on SQL Server Enterprise
There is no change in the default installation path for the Spotlight Diagnostic Server on upgrade from Spotlight on SQL Server

```
C:\Program Files\Quest Software\Diagnostic Server
```

The default file path of the Spotlight Client on upgrade from Spotlight on SQL Server is as before

```
C:\Program Files (x86)\Quest Software\Spotlight on SQL Server
```

The default file path of the Spotlight Client on a clean install (not an upgrade) is

```
C:\Program Files (x86)\Quest Software\Spotlight Enterprise
```


### Spotlight on SQL Server Enterprise 11.2 and alarms requiring acknowledgment
The Spotlight factory settings for alarms requiring acknowledgment changes on upgrade from Spotlight on SQL Server Enterprise 11.2. Only Connection Failure alarms are now factory set to require acknowledgment.

The alarms that were factory set to require acknowledgment in Spotlight on SQL Server Enterprise 11.2 and earlier are as follows. They are included here so you can choose to manually enable them to require acknowledgment again post upgrade if required.

*  Availability Group - Failed Over
*  Clusters - Failed over
*  Error Log - Error Count
*  LiteSpeed Backup Failed
*  LiteSpeed Backup Warning
*  Locks - Blocked Processes
*  Locks - Deadlocks
*  Mirroring Failedover
*  SQL Agent - Jobs Failed

### Spotlight on SQL Server Enterprise 11.1.x or earlier and Spotlight Cloud Mobile
If you used Spotlight on SQL Server 11.1.x or earlier to monitor your Spotlight connections on a mobile device and intend to continue monitoring your connections on a mobile device then the following additional upgrade instructions are required.

1. Uninstall the **Spotlight Web Publisher** via **Windows \| Control Panel \| Programs and Features**. The Spotlight Web Publisher was required in the past to monitor SQL Server connections on a mobile device. It is now important that you uninstall it. By default the Spotlight Web Publisher was installed on the same computer as the Spotlight Diagnostic Server.

2. From the Spotlight Client, click **Configure \| Spotlight Cloud**. Select **Upload data to Spotlight Cloud**. Ensure your Quest account details are correct.

{% include links.html %}
