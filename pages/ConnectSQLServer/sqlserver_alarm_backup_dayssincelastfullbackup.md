---
title: Backup - Days Since Last Full Backup Alarm
last_updated: July 29, 2016
summary: "The Backup - Days Since Last Full Backup Alarm becomes active when Spotlight detects that a full backup on the SQL Server database has never taken place or has not taken place in the last three days."
sidebar: c_sqlserver_sidebar
permalink: sqlserver_alarm_backup_dayssincelastfullbackup.html
id: alarm_backup_dayssincelastfullbackup
folder: ConnectSQLServer
---

This is a test edit by Steve... please discard.

{% include note.html content="This alarm is not activated for missing backups of the tempdb database." %}

When this alarm is raised, you should:

*   Check the date and time of the last backup from the **Databases** drilldown \| **Databases** grid.
*   Ensure you have appropriate backups of all necessary databases.

To configure the Backup - Days since Last Full Backup alarm

*  On the Spotlight home page, right-click the **Databases** button and select **Alarm Settings**
*  Select **Backup - Days since Last Full Backup**
*  Select **Override the default settings for the alarm**

Use the Severity table to customize the number of days and the severity. By default 0 to 3 days is Normal. A High severity alarm is raised after 3 days. Click in the table to edit the values. Decimal values can be used to indicate portions of a day. For example you could edit the table to raise a high severity alarm after 3.5 (3 and a half) days or 3.25 (3 and a quarter days).

To exclude certain databases, in the lower right pane, in **Do not raise an alarm for certain values**, click the **values** link to add the name of the database you want excluded.


By default, the following databases are automatically excluded from the Backup alarms:

*   model
*   pubs
*   Northwind
*   AdventureWorks
*   QuestSoftware
*   QuestWorkDatabase
*   tempdb

{% include links.html %}
