---
title: Diagnose alarms in Spotlight Enterprise
keywords: alarms
summary: "Show performance statistics (grids and charts) related to the raised alarm."
sidebar: p_enterprise_sidebar
permalink: enterprise_alarm_diagnose.html
folder: SpotlightEnterprise
---

An alarm is raised when a collected value falls outside its "normal" range of values. This "normal" range is defined by thresholds and severities [configured][enterprise_cfgmonitor_alarms] for the alarm. A new alarm is raised each time the severity for the alarm changes. When the severity returns to normal, the alarm is canceled. Alarms critical to your operation can be configured to remain on view until they are [acknowledged][enterprise_alarm_acknowledge].

## Displays for Spotlight alarms

[Heat map][enterprise_display_heatmap] | The Heat Map organizes connections based on the comparative number and severity of alarms raised against them. The Heat Map answers the question: Which monitored connections require the most urgent attention?
[Spotlight today][enterprise_display_spotlighttoday] | Spotlight Today is a display of recent alarms and alarms requiring acknowledgment.
[Alarms by time][enterprise_display_alarmsbytime] | Alarms by Time tracks the start time, duration, and severity of logged alarms.
[Alarm log][enterprise_display_alarmlog] | The alarm log is a display of logged alarms.
[Spotlight Overview page][enterprise_display_overview] | The Spotlight Overview page illustrates the flows and components of a single monitored connection. The flows and components are updated in real time to highlight obvious bottlenecks and problem areas and color coded to indicate when an alarm is raised.
[Playback][enterprise_display_playback] | Use the Playback facility to view events and data collected in the recent past on a Spotlight Overview Page, Drilldown or Spotlight Today. Playback time to capture the event or moment in Spotlight as though it was happening in real time.

## Act on (resolve, investigate) a raised alarm

From the Spotlight Overview page or Alarm log, right click on the component / alarm and select **What's this?** to investigate the alarm by the following options.

Icon | Title | Description
--------------|----------|------------
{% include inline_imageClient.html file="tb_whatsthis_diagnose.png" alt="Diagnose" %} | Diagnose Connection drilldowns | Show performance statistics ([grids][enterprise_display_grids] and [charts][enterprise_display_charts]) related to the raised alarm.
{% include inline_imageClient.html file="tb_whatsthis_acknowledge.png" alt="Acknowledge" %} | [Acknowledge][enterprise_alarm_acknowledge] | Acknowledge the alarm. This is appropriate for alarms that are configured to require acknowledgment.
{% include inline_imageClient.html file="tb_whatsthis_alarmhistory.png" alt="Alarm History" %} | [Alarm History][enterprise_display_alarmsbytime] | Show the alarm in Alarms by Time.
{% include inline_imageClient.html file="tb_whatsthis_snooze.png" alt="Snooze" %} | [Snooze][enterprise_alarm_snooze] | Temporarily remove the visual alert associated with the alarm.
{% include inline_imageClient.html file="tb_whatsthis_ignore.png" alt="Ignore" %} | [Ignore][enterprise_alarm_ignore] |  Configure Spotlight to ignore the alarm and future cases of the alarm. Select the rule by which you want Spotlight to ignore future cases: ignore this alarm for the current value or for the current connection. The choices are dependent on the type of alarm. This is a simplified interface for [Do not alarm for certain values][enterprise_cfgmonitor_alarm_ignorevalues].
{% include inline_imageClient.html file="tb_whatsthis_alarmsettings.png" alt="Alarm Settings" %} | [Alarm Settings][enterprise_cfgmonitor_alarms] | Configure the thresholds and severities that determine when the alarm is raised.


## Color

Spotlight uses color to identify the severity of an alarm. The alarm, Spotlight Overview page component or connection is colored. If more than one alarm is raised against the component or connection then the color shows the highest severity alarm raised.

Default Color | Severity
--------------|---------
{% include inline_imageClient.html file="icon_alarm_gray.png" alt="Disabled color" %} | Disabled
{% include inline_imageClient.html file="icon_alarm_green.png" alt="Normal color" %} | Normal / No alarm is currently raised.
{% include inline_imageClient.html file="icon_alarm_blue.png" alt="Information color" %} | Information
{% include inline_imageClient.html file="icon_alarm_yellow.png" alt="Low color" %} | Low
{% include inline_imageClient.html file="icon_alarm_orange.png" alt="Medium color" %} | Medium
{% include inline_imageClient.html file="icon_alarm_red.png" alt="High color" %} | High

Alternative colors for alarm severity are available. For more information, see [Severity colors for accessibility][enterprise_cfgclient_severitycolorsforaccessibility].

## Configuration
Many options are available from the Spotlight Client Configure ribbon. In particular:

[Configure \| Alarms][enterprise_cfgmonitor_alarms] | Set the thresholds and severities that determine when an alarm is raised. Disable an alarm. Set an alarm to require acknowledgment. Configure keyed alarms. Collect additional diagnostic information on an alarm.
[Configure \| Alarm Actions][enterprise_cfgmonitor_alarmactions] | Set actions for Spotlight to take when an alarm is raised. The actions Spotlight can take include running a program and sending an email. Conditions on taking the action can be defined, such as the day of the week, the time of day, the severity of the alarm, the alarm type and the connection type.

## About each alarm
Information about each alarm is documented under the connection type.

<ul>
{% assign sorted_pages = (site.pages | sort: 'title') %}
{% for page in sorted_pages %}
{% for tag in page.tags %}
{% if tag == "alarms_by_connection_type" %}
<li><a href="{{ page.url | remove_first:'/' }}">{{page.title}}</a></li>
{% endif %}
{% endfor %}
{% endfor %}
</ul>

## Relationship between alarms and schedule
See [Rules procedure intervals][RulesProcedureIntervals.html]




{% include links.html %}
