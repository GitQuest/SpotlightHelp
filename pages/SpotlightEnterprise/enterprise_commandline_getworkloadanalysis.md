---
title: Windows Powershell / Get Workload analysis Command line
summary: "Get Workload analysis Windows Powershell / the command line."
sidebar: p_enterprise_sidebar
permalink: enterprise_commandline_getworkloadanalysis.html
folder: SpotlightEnterprise
---



## Get Workload analysis commands

### Get-Workloadanalysis

Export the workload Analysis statement to a CVS file.

Command parameters

Parameter | Use
----------|----
-ConnectionName | The SQL Instance Technology name, case insensitive.
-StartDate | the start time of the data.
-EndDate | the end time of the data.
-Resource | "CPU", "Durations", "Logic Reads", "Physical Reads", "Writes".
-Path | the output file saved path, the default path is the current run command path.
-isSQL2008 | If the SQL version is 2008 or 2008R2, this parameter is required.
-DS | The Diagnostic Server address.

Export the CSV file to the current path

```
Get-Workloadanalysis -connectionname W2K16-SQL16_sqlserver -startdate "2020-10-23 5:30:00" -enddate "2020-10-23 6:30:00" -Resource "CPU"
```

Export the CSV file to a specific path

```
get-workloadanalysis -connectionname W2K16-SQL16_sqlserver -startdate "2020-10-23 5:30:00" -enddate "2020-10-23 6:30:00" -Resource "CPU" -Path "C:\sosse"
```

The instance is SQL Server 2008 or 2008R2

```
get-workloadanalysis -connectionname SQL2008R2SP3_sqlserver -startdate "2020-10-16 2:30:00" -enddate "2020-10-16 6:30:00" -Resource "Reads" -isSQL2008
```


{% include links.html %}
