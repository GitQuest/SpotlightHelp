---
title: Configure PagerDuty
summary: "Enter PagerDuty account details for the Spotlight Diagnostic Server (to fulfill on Configure | Alarm Actions | Alarm Action | Send PagerDuty incident)."
sidebar: p_enterprise_sidebar
permalink: enterprise_cfgds_pagerduty.html
id: 709
folder: SpotlightEnterprise
---



## PagerDuty and Spotlight

Prior to following these instructions ensure you have your PagerDuty Integration Key. The instructions in the Spotlight Enterprise Integration Guide on the PagerDuty web site provide you with the necessary steps: [https://www.pagerduty.com/docs/guides/quest-spotlight-enterprise-integration-guide/](https://www.pagerduty.com/docs/guides/quest-spotlight-enterprise-integration-guide/). PagerDuty is a third party product ([www.pagerduty.com](https://www.pagerduty.com/)).

The Spotlight Diagnostic Server requires Internet access in order to fulfill on [Configure \| Alarm Actions \| Alarm Action \| Send PagerDuty incident][enterprise_cfgmonitor_alarmaction].

{% include note.html content="Spotlight is integrated with PagerDuty Event API V1" %}

## Open this screen from the Spotlight Client

1. Click **Configure \| Diagnostic server**.
   {% include imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %}
2. Select **Configure PagerDuty**.

## Select the Diagnostic Server

For federated Spotlight Diagnostic Server you will be prompted to select the Spotlight Diagnostic Server to configure. Each Spotlight Diagnostic Server is independently configured for pager duty.

## Specify your PagerDuty account details.

### Integration Key

The Integration Key authenticates the Spotlight Diagnostic Server to your PagerDuty account.



## Click Trigger Test Incident

Click **Trigger Test Incident** to verify the Spotlight Diagnostic Server can successfully send an incident report to PagerDuty.

{% include note.html content="PagerDuty receives incident reports from the Spotlight Diagnostic Server according to the Alarm Action Rules set in the Alarm Action Editor. No incident reports are sent until you create and enable appropriate rules. See [Configure \| Alarm Actions][enterprise_cfgmonitor_alarmactions]." %}



{% include links.html %}
