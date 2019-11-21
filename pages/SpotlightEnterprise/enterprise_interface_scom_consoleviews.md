---
title: SCOM Console views of Spotlight
summary: "SCOM Console views of Spotlight include a Dashboard, Diagnostic Servers' Health and Spotlight Alarms."
sidebar: p_enterprise_sidebar
permalink: enterprise_interface_scom_consoleviews.html
folder: SpotlightEnterprise
---


## SCOM Console views
Open the SCOM Console. Expand **Monitoring \| Quest Spotlight Enterprise**. Select from the available SCOM Console views.

{% include note.html content="The views in the SCOM Console update automatically when an alarm is raised or the alarm status changes. The views in the SCOM Console show all Spotlight connections, including those connections that are disabled and in outage." %}

## Dashboard

Select to show the Spotlight Diagnostic Servers known to SCOM, the connections monitored by each Spotlight Diagnostic Server and the alarms raised for each connection.

To add a Spotlight Diagnostic Server to SCOM see [Configure the Spotlight Management Pack for SCOM][enterprise_interface_scom_cfg].

## Diagnostic Servers' Health

Select to show alarms raised against each Spotlight Diagnostic Server. For example, show:

* Health check data upload alerts
* Mobile monitoring data transfer failure alerts
* Failure to monitor the Spotlight connection
* Failure to send email notifications of alarms raised

## Spotlight Alarms

Select to show in detail alarms raised against monitored Spotlight connections.

* Show the alarm, the severity of the alarm, the connection the alarm is raised against, a descriptive message of the alarm, the date and time the alarm was raised.
* Snooze / Unsnooze the alarm. If the alarm is snoozed, show the date and time the alarm is snoozed until.
* Acknowledge the alarm.




{% include links.html %}
