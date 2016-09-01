---
title: ﻿Monitored Server - SQL Server Host Not Defined Alarm
last_updated: July 29, 2016
summary: ""
sidebar: c_sqlserver_sidebar
permalink: sqlserver_alarm_monitoredserver_hostnotdefined.html
id: alarm_ms_sqlserverhostnotdefined
folder: ConnectSQLServer
---



The **Monitored Server - SQL Server host not defined** alarm is raised for:

1. A Microsoft Cluster Server (MSCS)
2. Where the **SQL Server Connection Details** dialog **Connection** field is set to **Cluster (monitor active node)**.
3. And the active cluster node is NOT in the list of available OS connections in the **SQL Server Connection Details** dialog **Linked OS Connection** drop down field.

For a SQL Server cluster that uses the Cluster (monitor active node) feature there must be a Windows connection for each Windows node in the cluster. See the online help **Spotlight \| Spotlight on SQL Server \| Connections to SQL Servers** page for more information. This alarm  clears once the Windows connection has been created.


The Monitored Server - SQL Server Host Not Defined Alarm is raised for:

* A Microsoft Cluster Server (MSCS)
* Where the SQL Server Connection Details dialog Connection field is set to Cluster (monitor active node).
* And the active cluster node is NOT in the list of available OS connections in the SQL Server Connection Details dialog Linked OS Connection drop down field.


For a SQL Server cluster that uses the Cluster (monitor active node) feature there must be a Windows connection for each Windows node in the cluster. For more information, see SQL Server \| Connection Details. This alarm clears once the Windows connection has been created.

{% include links.html %}
