---
title: Index Fragmentation alarm
tags: [sqlserver_alarms]
last_updated: July 29, 2016
summary: "The Index Fragmentation alarm is raised when the largest Index file on the SQL Server is more than 5% fragmented. It is a good idea to defragment large index files that are more than 5% fragmented."
sidebar: c_sqlserver_sidebar
permalink: sqlserver_alarm_index_fragmentation.html
id: Index_Fragmentation.Alarm
folder: ConnectSQLServer
---


{% include note.html content="Spotlight only checks large index files, that is Index files that have over 1000 pages." %}


When the alarm is raised:

1. Open the **SQL Server \| Databases drilldown \| Fragmented Indexes**.
2. Select the index to defragment and click **Fragmented Indexes \| Generate defragmentation script**.
3. Use SQL Server Management Studio to schedule a job to run this script during a quiet period.


{% include tip.html content="Choose a quiet time to run this script. Execution of this script could put significant load on the SQL Server." %}

{% include links.html %}
