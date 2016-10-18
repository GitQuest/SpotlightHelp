---
title: Spotlight Mobile Summary
summary: "Spotlight Mobile monitoring features include a Heatmap, alarm list, alarm details and the ability to snooze and acknowledge alarms."
sidebar: p_mobile_sidebar
permalink: mobile_summary.html
folder: SpotlightMobile
---


Screen / Action | Android | iPhone | Description
----------------|---------|--------|------------
Heatmap | | | The Heat Map organizes connections based on the comparative number and severity of their alarms. Connections with the most alarms raised against them are given the most surface area. Tap a connection to list all alarms currently raised against that connection.
Alarm list | | | List the alarms currently raised against a connection or connection view. Tap an alarm for more details.  
Sort / Group Alarms | ![Sort Android]({{ "/imagesMobile/tap_android-sort-icon.png" | prepend: site.baseurl }}) | ![Sort iPhone]({{ "/imagesMobile/tap_iOS-sort-group-alarms.png" | prepend: site.baseurl }}) | Sort or group alarms on the Alarm List. Sort by date or severity. Group by server, severity or alarm.
Acknowledge Alarm | ![Ack Android]({{ "/imagesMobile/tap_android-ack-icon.png" | prepend: site.baseurl }}) | ![Ack ios]({{ "/imagesMobile/tap_Ack-button-iOs.png" | prepend: site.baseurl }}) | Acknowledge an instance of an alarm requiring acknowledgment.
Snooze Alarm | ![Snooze Android]({{ "/imagesMobile/tap_android-snooze-icon.png" | prepend: site.baseurl }}) | ![Snooze iPhone]({{ "/imagesMobile/tap_iOS-snooze-icon.png" | prepend: site.baseurl }}) | Temporarily remove the visual alert associated with an alarm.  
Connections and connection views | ![Connections Android]({{ "/imagesMobile/tap_android-connection-nav-icon.png" | prepend: site.baseurl }}) | ![Connections iPhone]({{ "/imagesMobile/tap_iOS-connection-nav-icon.png" | prepend: site.baseurl }}) | Access the views of your enterprise: heatmaps, alarm lists and connection views. Create new Heatmap or Alarm list views.
Spotlight overview page | ![overview Android]({{ "/imagesMobile/tap_android-homepage-icon.png" | prepend: site.baseurl }}) | ![overview iPhone]({{ "/imagesMobile/tap_iOS-homepage-icon.png" | prepend: site.baseurl }}) | Show the Spotlight overview page panels for the connection.
Playback | ![Playback]({{ "/imagesMobile/tap_playback-icon_iphone.png" | prepend: site.baseurl }}) | ![Playback]({{ "/imagesMobile/tap_playback-icon_iphone.png" | prepend: site.baseurl }}) | Reproduce the Spotlight overview page for a date and time from the recent past.
Settings | ![Settings Android]({{ "/imagesMobile/tap_android-settings-icon.png" | prepend: site.baseurl }}) | ![Settings iPhone]({{ "/imagesMobile/tap_iOS_settings_icon.png" | prepend: site.baseurl }}) |  Configure Spotlight Mobile.
Profile | ![Profile Android]({{ "/imagesMobile/tap_android-users-profile-icon.png" | prepend: site.baseurl }}) | ![Profile iPhone]({{ "/imagesMobile/tap_iOS-users-profile-icon.png" | prepend: site.baseurl }}) | Show / change the current user. This is applicable where more than one Spotlight Cloud user has signed in to Spotlight Mobile.
Refresh | ![Refresh Android]({{ "/imagesMobile/tap_android-refresh-icon.png" | prepend: site.baseurl }}) | ![Refresh iPhone]({{ "/imagesMobile/tap_iOS-refresh-icon.png" | prepend: site.baseurl }}) | Refresh the screen. The time and date of the last refresh is on display. From time to time the refresh button may be grayed out (disabled).

## Color

The alarm, connection or connection view is colored according to the most severe current alarm.

Default Color | Severity | Description
--------------|----------|------------
{% include inline_imageMobile.html file="icon_alarm_green.png" alt="Normal color" %} | Normal | No alarms are raised against this connection.
{% include inline_imageMobile.html file="icon_alarm_blue.png" alt="Information color" %} | Information | At least one information alarm is raised against this connection. No other alarms are raised.
{% include inline_imageMobile.html file="icon_alarm_yellow.png" alt="Low color" %} | Low | At least one low severity alarm is raised against this connection. No high or medium severity alarms are raised.
{% include inline_imageMobile.html file="icon_alarm_orange.png" alt="Medium color" %} | Medium | At least one medium severity alarm is raised against this connection. No high severity alarms are raised.
{% include inline_imageMobile.html file="icon_alarm_red.png" alt="High color" %} | High | At least one high severity alarm is raised against this connection.

{% include links.html %}
