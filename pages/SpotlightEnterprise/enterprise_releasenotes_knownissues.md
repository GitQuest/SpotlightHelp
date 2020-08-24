---
title: Known issues with this release
keywords: release notes
summary: "The following is a list of issues, including those attributed to third-party products, known to exist at the time of release."
sidebar: p_enterprise_sidebar
permalink: enterprise_releasenotes_knownissues.html
folder: SpotlightEnterprise
readonly: true
---

## General known issues

Known Issue | Issue ID
------------|---------
Spotlight Clients installed on Windows 10 - Exception error may occur on deleting two connetions at the same time. | SOSSE-6556
If the Spotlight Client looses connection to the Spotlight Diagnostic Server then after a period of days the Spotlight Client will develop a minor memory leak. <br><br>*Workaround:* Restart the Spotlight Client. | 5433
The Spotlight Client can experience performance issues (opening the home page, acknowledging and snoozing alarms) when a large number of alarms are raised against the one connection. | 2651
Manual refresh is required on some drilldowns. Right click the data in the grid and select **Restore Default Settings \| Restore**. The grid shows "Loading". Click Refresh to populate the grid. | 11333 <br><br> 11406
Known issues using the online help top navigation pane from the following operating systems: Microsoft Windows Server 2008 R2 to 2019. *Workaround:* Configure the Spotlight Client to use offline help as per **Configure \| Spotlight \| Troubleshooting \| Choose Help location** or disable IE Enhanced Security Configuration from the Server Manager. Disabling IE Enhanced Security Configuration is not the preferred option. | SOSSE-6580
Known issues using Spotlight Help when Internet Explorer 8 or below is installed on the Spotlight Client host computer. *Workaround:* Upgrade Internet Explorer on the Spotlight Client host computer. | SOSSE-6581


## known issues with installation and upgrade

Known Issue | Issue ID
------------|---------
On upgrade to Spotlight Enterprise 12.1, there is a significant difference in the way data is aggregated for the SQL Server \| Workload Analysis and Wait Events drilldowns. When the selected time range includes data collected prior to the upgrade, that data may not display properly. As a workaround, adjust the time range to include only post upgrade data. | DS-824
**Installing other Spotlights.** Do not install other Spotlights into the Spotlight Enterprise folder. You will be unable to run Spotlight Enterprise if you do this. When installing other Spotlights you must install them into a different folder. | N/A
**Remote installation.** Remote installation of Spotlight Enterprise fails if the user has both a domain account and a local account with the same user name. | N/A


## known issues with the Spotlight Diagnostic Server

Known Issue | Issue ID
------------|---------
**Federation.** If you remove and then re-add a Spotlight Diagnostic Server to the federation, the Spotlight Connections from the "re-added" Spotlight Diagnostic Server will display in the Spotlight Client as if disabled (color gray). <br><br>*Workaround:* Restart the Spotlight Client. | 5432
**System time changes.** Stop the Diagnostic Server service before changing the system time on the Diagnostic Server machine. | N/A
**Moving a Diagnostic Server.** If you want to move your Diagnostic Server to a different host machine and continue to use the current Spotlight Statistics Repository, you will not be able to report on data collected across the original and moved Diagnostic Servers. Contact Quest Support for assistance if you want to report on data collected by the original Diagnostic Server after the move. | 4178
**Renaming the Diagnostic Server.** The Diagnostic Server host cannot be renamed without reinstalling the Diagnostic Server. To conserve configuration and history, migrate the Diagnostic Server to another host before the machine is renamed. | 3052
**Diagnostic Server user privileges.** The minimum Windows privilege level required to run the Diagnostic Server is Power User. During runtime, the Diagnostic Server requires write access to folders in the install directory. Without the appropriate privileges, the Diagnostic Server cannot run. | 206558



## known issues using playback

Known Issue | Issue ID
------------|---------
**History Browser and Playback mode.** Playback data is collected at scheduled intervals, in response to some alarms, and also while viewing a drilldown using the Spotlight client. This means that history data may not be available for a drilldown in Playback mode. To change the rate at which data is collected, go to **Configure \| Scheduling**. | N/A
The **Show System Sessions** filter is not supported in Playback mode. | SoSSE-7031


## known issues using the Spotlight Statistics Repository

Known Issue | Issue ID
------------|---------
**Documentation of the Collections used by Reports** - All reports source their data from the collections stored in the Spotlight Statistics Repository. The direct relationship between report component and spotlight collection is documented in the Spotlight help for a subset of the available reports. | 5258
**Unable to select connections for views and reports** - The Spotlight Statistics Repository may have corrupted on upgrade. Perhaps connection to the Spotlight Statistics Repository was lost during creation; leaving the database in an inconsistent state. <br><br> *Workaround* - Drop the Spotlight Statistics Repository database. From the Spotlight Client, Configure \| Diagnostic Server \| Configure the Spotlight Statistics Repository to create a new Spotlight Statistics Repository. | 5216
**Collection scheduling and Reporting and Trending.** Scheduling a collection to run at different time periods for two or more monitored servers can cause gaps in the Reporting and Trending charts for multi-server views. | 6362
**Storing statistics in the Spotlight Statistics Repository.** The Store statistics in the Spotlight Statistics Repository option applies to both the SQL Server connection and its equivalent Windows connection. If you change this option for a SQL Server connection, the change is also applied to the equivalent Windows connection. | N/A



## known issues configuring Spotlight

Known Issue | Issue ID
------------|---------
**Spotlight Alarm Actions** does not have an action to kill a block process. <br><br> *Workaround:* Write a SQL Query to return the SPID and kill the process; put the SQL into the Execute a SQL Script action. | 2669
**Unable to send email** - This is a known issue under the following circumstances <br><br> Symantec Endpoint Protection is installed on the Spotlight Diagnostic Server and <br> The Spotlight Diagnostic Server is installed on a 64 bit machine and <br> The Spotlight Diagnostic Server installation is 64-bit. <br><br> *Workaround:* "disable the Internet Email Auto-Protect option" in Symantec Endpoint Protection. See also: <br> http://www.symantec.com/business/support/index?page=content&id=TECH95093 and <br> http://www.symantec.com/connect/forums/sep-121-internet-email-auto-protect-and-ccnet-mail-issues | 2266
**Spotlight Cloud** - On the Configure \| Spotlight Cloud page, the organization name or the text "My Organization" may be displayed instead of the email address for customers who signed in to Spotlight Cloud using Spotlight Enterprise versions earlier than 12.2. | ENT-217
**Cap on collections.** To limit Spotlight's load and memory consumption, a cap of 10000 rows is placed on most collections. To modify this cap, edit the following text in file ..\agent\bin\DiagnosticServer.properties: <br><br> "-Dcom.quest.adk.rowLimit=10000" | 11685
**Unable to receive email attachment** - If the Spotlight Diagnostics Server sends an email with an attachment, that attachment will have a .zip extension. Some email servers automatically reject attachments with a .zip extension. <br><br> *Workaround* - Change the .zip extension to something else. In the Spotlight Diagnostic Server installation folder, in the **Agent/conf** folder, modify the text file **DiagnosticServer.properties** by changing the value of the property **com.quest.adk.email.attachment.extension**. | SOSSE-5698
**Manage access to Spotlight connections.** If two Spotlight Clients are connected to one Diagnostic Server, unassigning a connection in one Client and then accessing this connection from the other Client will pop up an error. <br><br> *Workaround:* Restart the other Spotlight Client. | SOSSE-8232
**Manage access to Spotlight connections.** For efficiency reasons the Diagnostic Server only checks Active Directory group membership periodically. <br><br> In the following scenarios a user may still have access to connections affected by a blacklist <br><br> 1. An Active Directory group is removed from or added to a Diagnostic Server group. <br> 2. The user is removed from or added to a Diagnostic Server group.<br><br> *Workaround:* Restart the Spotlight Client. After that the change should take effect. | SOSSE-8222
**Manage access to Spotlight connections.** A Windows user with Non ASCII characters in any of the three groups Spotlight Diagnostic Administrators, Spotlight Diagnostic Users and Spotlight Diagnostic Read-Only Users is not being recognized and displayed properly. However the issue only happens in Manage access to Spotlight connections and it does not affect any other Spotlight features. <br><br> *Workaround:* Do not use Non ASCII characters for the users who require access to Spotlight. | SOSSE-8203
**Manage access to Spotlight connections.** If a user is granted access to a SQL Server connection but is denied access to the associated Windows connection Spotlight still shows Windows alarms in the alarm editor when the SQL Server connection is selected in the editor. | SOSSE-8199     
**Manage access to Spotlight connections.** If a user is granted access to an Analysis Services connection but is denied access to the associated Windows connection Spotlight still shows the Windows metrics on the overview page of the Analysis Services connection. | SOSSE-8199
**Manage access to Spotlight connections.** The Spotlight Client can add an existing connection although it is in the blacklist. On attempting to monitor this connection there will be no visible data and the monitoring components will be disabled. <br><br> *Workaround:* Restart the Spotlight Client to remove the connection from Spotlight displays. Contact an Administrator to obtain access to monitoring the connection. | SOSSE-8189     


## Monitoring Connections

### known issues monitoring SQL Server Analysis Services

Known Issue | Issue ID
------------|---------
GMT Time Zone: The Diagnostic Server shows the wrong time. The Activity drilldown, Connections page may show the wrong time in the GMT Time Zone by incorrectly adjusting for DST. | 10433


### known issues monitoring SQL Server

Known Issue | Issue ID
------------|---------
For all Error Log alarms the option to 'Ignore for this value only' does not work. | DS-1174
The Workload Analysis and Wait Events drilldowns do not show data properly when upgrading from Spotlight versions 11.7.1 and below to Spotlight Enterprise 12.1. | DS-1070
Historical information is not kept for the **Wait Statistics drilldown**. There is no workaround.<br><br>Historical information is not kept for the **SQL Server Wait Statistics Report**. If access to the report data is required please contact Quest Support. | SOSSE-6388
On the **SQL Activity drilldown \| Query Execution Statistics page** the **Query Plan** column is empty for longer query plans (plans exceeding 43679 characters). *Workaround:* Right click on the blank query plan cell and select to copy the current cell to the clipboard. | SOSSE-6535
Playback is not currently available for the SQL Server **Databases drilldown \| Fragmented Indexes page**. | SOSSE-6560
**Overview Page** - An unexpected error occurs the first time the SQL Server Overview page is opened in the Spotlight client session. <br><br> Performance Health / Wait Events / Workload Analysis - drilldown showd no data. <br><br> *Workaround:* Apply patch to .NET 4 - Software Update KB2468871v2 <br><br> See also own Known issues configuring Spotlight 3606. | 3606
**No Disk Space data on Unix/Linux Operating System** - The SQL Server \| Databases drilldown shows no Disk Space data when the SQL Server is hosted on a Linux operating system. The following alarms don't work: Databases - Dynamic Data File Group Growths Remaining, Databases - Dynamic Log File Growths Remaining, Databases - Data File Group Space Used, Databases - Log File Space Used. The reason for this issue is Microsoft does not yet support retrieval of this data on Linux. | DS-476
**Spotlight Reports where SQL Server is hosted on Unix/Linux** Some Spotlight Reports for SQL Server are not supported where the SQL Server host is Unix/Linux. |
**The Spotlight Discovery Wizard where SQL Server is hosted on Unix/Linux** Spotlight does not discover SQL Server instances hosted on Unix/Linux. |
**SQL Server drilldowns where SQL Server is hosted on Unix/Linux** The following drilldowns are not supported for SQL Server instances hosted on Unix/Linux: SQL Activity \| Custom Counters, High Availability, Support Services, Databases \| Disk Space, Error Log \| SQL Agent Error Logs |
**SQL Server 2012 and above** - Spotlight does not support Analysis Services in Tabular and Sharepoint modes. | .
**Workload Analysis drilldown** - SQL Server 2012 and above - When monitoring a failover cluster the Physical Reads value is 0 / No Data. | 3688
**Workload Analysis and Wait Events drilldowns** - Unable to copy and paste queries from these drilldowns when Internet Explorer 8 or below is installed on the Spotlight Client host computer. Workaround: Upgrade Internet Explorer on the Spotlight Client host computer. | 6677
**Workload Analysis and Wait Events drilldowns - SQL Server versions prior to 2012** - On configuring Spotlight to exclude Spotlight sessions from the Wait Events and Workload Analysis drilldowns, Spotlight metrics and waits still show in the current data. For SQL Server versions prior to 2012 the way the exclusion is done is that only one session is excluded by the Extended Events collections. However Spotlight makes at least two connections to SQL Server so there can be multiple sessions; data can still be collected for those other sessions. This is a limitation imposed by the fields available in Extended Events in older SQL Server versions. | SOSSE-6913
**SQL Server 2012 and SQL Server 2008 R2** - "Using dbghelp.dll version 4.0.5" entries in the SQL Server Error Log. The source of these entries can be traced back to a known issue (Microsoft) when a statement or job executes the sys.fn_xe_file_target_read_file stored procedure. Refer to http://support.microsoft.com/kb/2878139 <br><br> The Spotlight SQL Server \| Performance Health feature uses XEvents sessions which may execute the sys.fn_xe_file_target_read_file stored procedure. | 2927
In the SQL Server Error Log, entries "SQL Trace was started" and "SQL Trace was stopped." repeat every 10 minutes while Spotlight is monitoring the connection. These entries are added by Microsoft; Spotlight Enterprise uses SQL Trace to monitor for deadlocks. | 3582
**SQL Server 2008 R2** For database type FILESTREAM the value "Total MB" for the database always shows as 0. | DS-1419
**Monitoring SQL Server 2008 RTM.** The Deadlocks page (SQL Activity drilldown) may not show data when monitoring a SQL Server 2008 RTM database. <br><br> *Workaround:* Upgrade to SQL Server 2008 SP1 | 7495
**Access errors when connecting to SQL Server 2005.** If an access error related to xp_cmdshell occurs and the user changes the SQL Server configuration to allow access to xp_cmdshell, the SQL Server documentation states that you must disconnect and reconnect. To disconnect in Spotlight Enterprise, you must disable monitoring and enable monitoring for that SQL Server. <br><br>In the Spotlight Browser, right-click the SQL Server connection and select Properties. On the Monitoring page, clear the Monitor this server option and click OK. Open the Monitoring page again and select Monitor this server and then click OK. | N/A
Unexpected error **"Could not load file or assembly 'System.Cor, Version=2.0.5.0…"** on first time connecting to a SQL Server instance. <br><br> *Solution:* Install the following patch to the .NET framework (http://support.microsoft.com/kb/2468871) | 2764
The collections Fragmentation by Index and Fragmentation Overview can adversely impact the performance of monitored SQL Servers. If this is an issue then use Configure \| Scheduling to reduce the frequency of collection | 2705
**Deadlock List Report** - Each Deadlock List report is limited to 4000 characters of deadlock information. | 13064
**Error collecting data.** The collection used to populate the Query Execution Statistics drilldown is unable to run when some databases on the instance are in restricted states of access (for example, Single User Mode, Offline). | 7584
**Query Execution Statistics drilldown** - Query Plan returns a duplicate attribute error - This is a Microsoft bug. <br><br> *Workaround:* Restrict the grid by getting fewer records or sorting on a different variable. | 11179
For SQL Activity \| Sessions \| Plan there is a limit on the size of the \<inputbuf\> tag of 1024 bytes (or nearly that). This cannot be expanded as the SQL Server truncates the SQL when it creates the XML. | 2300
**Negative values in Wait Statistics drilldown.** Negative values may be shown in the Waits Details grid. | 3757
**SQL - Long Running SQL alarm** raised from a Spotlight issued query - This issue follows "Cannot alter the event session", the query stops responding (hangs) so it raises a Long Running SQL alarm. Refer to the Microsoft known issue: https://support.microsoft.com/en-us/kb/2511963  | .


### known issues monitoring Windows Server

Known Issue | Issue ID
------------|---------
**WMI access denied alarm messages.** A large number of WMI access denied alarm messages usually indicates a network problem such as a malfunctioning domain controller or DNS server. When the network problem is resolved, restart the Diagnostic Server service. | N/A
**Microsoft Cluster Server connection problem.** If you are connecting to a Microsoft Cluster Server system that does not have control of all disk resources, the uncontrolled disks may display a value of zero for space in total and space available in Spotlight. To rectify this problem customize your disk view to not show this disk. (Do this by right-clicking the disk and choosing Disk Options) | N/A
**Disk Queue length metric.** Due to a bug in WMI, the Disk Queue length metric can briefly show a false high value when returning from a (valid) Disk Queue Length alarm. | 13227
**Missing data on the CPU drilldown** when monitoring a Windows 2008 R2 Server with more than 32 processors. *Workaround:* http://msdn.microsoft.com/en-au/en-us/library/windows/desktop/aa393067(v=vs.85).aspx | 14493
**Open Sessions grid.** Values displayed in the Elapsed Time and Idle Time columns in the Open Sessions grid (Network drilldown > Sessions tab) may not be accurate if the session has been running for more than 18 hours. | N/A
**Time stamp in Event Log drilldown.** When monitoring a Windows Vista 64-bit or Windows Server 2008 64-bit machine, the time shown for events in the Event Log drilldown is in GMT, not local time. | 4625
**Errors in the Windows Security Log.** Specifying OS Connection Details on Windows connections can cause WMI connection errors to be reported in the Windows Security Log of the machine being monitored. This does not affect Spotlight's monitoring capabilities. | 6722
**Unusually large values displayed in Spotlight.** Spotlight may display unusually large values on some components and charts. These values are incorrect and are due to inaccurate raw performance counter values returned by Microsoft Windows. The following components and charts are affected: <br> *Disk Queue Length chart* (Spotlight on Windows > Disks drilldown > Logical Disk Activity page and Physical Disk Activity page). <br> *Disk Load chart* (Spotlight on Windows > Disks drilldown > Logical Disk Activity page and Physical Disk Activity page). <br><br> *Workaround:* Reboot the machine returning large values. | 5796

### Known issues monitoring VMware

Known Issue | Issue ID
------------|---------
When connecting to VMware with Diagnostic Server credentials Spotlight connects successfully but does not show hosts on the VMware homepage. | DS-777

### known issues monitoring Unix/Linux Server

Known Issue | Issue ID
------------|---------
**Custom Counters** Custom Counters are not supported for Unix/Linux hosts. |  SOSSE-6363
**Spotlight Reports** Spotlight Reports for Reporting and Trending are not supported for the Unix/Linux Connection Type. |  SOSSE-6364
**Monitored Files** Spotlight can be configured to track the growth of files (usually log files) on monitored Windows Server. This service is not supported for the Unix/Linux Connection Type. |  SOSSE-6362
Data from the Unix/Linux operating system is not collected for the **Support Bundle**. |

{% include links.html %}
