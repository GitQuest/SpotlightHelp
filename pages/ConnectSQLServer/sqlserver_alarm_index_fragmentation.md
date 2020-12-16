---
title: Index Fragmentation alarm
tags: [sqlserver_alarms]
last_updated: July 29, 2016
summary: "The Index Fragmentation alarm is raised when the largest index partition on the SQL Server is more than 5% fragmented. It is a good idea to defragment large index partitions that are more than 5% fragmented."
sidebar: c_sqlserver_sidebar
permalink: sqlserver_alarm_index_fragmentation.html
id: Index_Fragmentation.Alarm
folder: ConnectSQLServer
---


{% include note.html content="Spotlight only checks large index partitions, that is index partitions that have exceeded the **Maximum Size** criteria (default 10MB). The Maximum Size criteria can be customized using the Connection Tags feature; refer to the **SQL Server \| Databases drilldown** documentation for more information." %}

When the alarm is raised:

1. Open **SQL Server \| Databases drilldown \| Fragmented Indexes**.
2. Select the index to defragment and click **Fragmented Indexes \| Generate defragmentation script**.
3. Use SQL Server Management Studio to schedule a job to run this script during a quiet period.


{% include tip.html content="Choose a quiet time to run this script. Execution of this script could put significant load on the SQL Server." %}

{% include links.html %}
