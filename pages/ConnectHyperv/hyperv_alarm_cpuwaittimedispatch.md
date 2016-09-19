---
title: Hyper-V CPU Wait Time Per Dispatch Alarm
last_updated: July 29, 2016
summary: "The CPU wait time per dispatch alarm is raised when the average queue time for the virtual machine waiting for CPU to become available exceeds a threshold."
sidebar: c_hyperv_sidebar
permalink: hyperv_alarm_cpuwaittimedispatch.html
id: alarm_hyperv_cpuwaittimedispatch
folder: ConnectHyperv
---



The average queue time should remain under 60,000ns. This alarm is raised when the average queue time exceeds 60ms. A high severity alarm is raised when the average queue time exceeds 100ms.

When the alarm is raised there is CPU starvation.

*  See the Windows Server \| CPU Drilldown \| Virtualized CPU page \| CPU wait time per dispatch chart.
*  See your Hyper-V administrator for ways to address this issue.


{% include links.html %}
