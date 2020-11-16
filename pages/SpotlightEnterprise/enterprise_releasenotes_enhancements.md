---
title: Enhancements in this release
keywords: release notes
summary: "The following is a list of enhancements implemented in Spotlight Enterprise 13.3"
sidebar: p_enterprise_sidebar
permalink: enterprise_releasenotes_enhancements.html
folder: SpotlightEnterprise
readonly: true
---

## Enhancements implemented in Spotlight Enterprise 13.3

Enhancement | Issue ID
------------|---------
Spotlight on SQL Server Enterprise is now FIPS 140-2 compliant. | SEMB-494
Plan visualization and plan analysis have been enhanced to show more optimization suggestions. | SEMB-463
Spotlight will send a resolve event to PagerDuty when an alarm is cleared. | SEMB-432, SOSSE-8697
The Wait Events and Workload Analysis drilldowns have been enhanced to show the procedure name instead of the SQL text. | SEMB-289, SOSSE-8805
The I/O stall alarm rule has been enhanced to reduce the alarm noise. | SEMB-561, SOSSE-8981
The Recompiles alarm rule has been enhanced to reduce number of alarms. | SEMB-560, SOSSE-8980
Updated the default Extended Events minimum duration from 0 to 200. | SEMB-585 , SOSSE-9021
Export data from the Workload Analysis collection using PowerShell. | SEMB-68
Give a warning when SNMP is configured to use an insecure connection. | SEMB-540
Give a message to show if the connection to the SMTP server is secure or not. | SEMB-628
Raise an alarm when the Linux/Unix connection is not secure. | SEMB-629
{% include links.html %}
