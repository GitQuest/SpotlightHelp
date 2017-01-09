---
title: Make (add to) a federation
summary: "The standard Spotlight configuration has one Spotlight Diagnostic Server. All connections are monitored through the Spotlight Diagnostic Server."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_federation_add.html
folder: SpotlightEnterprise
---

Start with two separate Spotlight deployments.

{% include inline_imageClient.html file="figure_federation_deployment-Project-0A.png" %}
{% include inline_imageClient.html file="figure_federation_deployment-Project-0B.png" %}

NOTE: A Spotlight Diagnostic Server can connect to one federation at a time. Remove a Spotlight Diagnostic Server from one federation before adding it to a different federation.

The Spotlight Diagnostic Servers in the federation cannot be monitoring the same connections. Where duplicate connections exist, federation cannot proceed. Spotlight will prompt you to delete duplicate connections.

Each Spotlight Diagnostic Server in the federation must be running Spotlight version 11.6 or later.

Each Spotlight Diagnostic Server in the federation authenticates with one selected Spotlight Diagnostic Server in the federation (the Configuration server). Each Spotlight Diagnostic Server authenticates with the Configuration server using Windows authentication over TCP port 40303. The Windows account that each Spotlight Diagnostic Server is running under must be valid in the domain of the Configuration server. Spotlight Diagnostic Server running under the built in Windows accounts (local system or network service) cannot be federated.

All Spotlight Clients in the federation retrieve monitoring information directly from the Spotlight Diagnostic Server. TCP port 3843 must be open for incoming connections from all Spotlight Diagnostic Server in the federation.

We suggest that a VPN is implemented with a federated system for increased security.

## Steps to make (add to) a federation

1. Open a Spotlight Client.

   If the federation already exists, open any Spotlight Client connected to the federation. When federating two separate Spotlight Diagnostic Server, open a Spotlight Client connected to either Spotlight Diagnostic Server.
2. From the Spotlight Client, click **Configure \| Diagnostic Server \| Federate Diagnostic Servers**.
3. Click **Add**. Select the host of the Spotlight Diagnostic Server. The Spotlight Diagnostic Server should be installed and operational and accessible to the Spotlight Client.


{% include imageClient.html file="figure_federation_Federation-of-DS.png" %}


## On adding a Spotlight Diagnostic Server to the federation

### Monitored connections
The Spotlight Clients connected to the Spotlight Diagnostic Server that has been added to the federation now connect to the federation of Spotlight Diagnostic Server. Spotlight Clients in the federation monitor connections from all Spotlight Diagnostic Server in the federation. Data to / from monitored connections is communicated directly from Spotlight Diagnostic Server to Spotlight Client. It is required that all Spotlight Clients have open communications with all Spotlight Diagnostic Server in the federation.

### Custom views
Spotlight Clients in the federation have access to all custom views in the federation. The custom views from the newly joined Spotlight Diagnostic Server will be accessible to all Spotlight Clients in the federation. Any two custom views with the same name will be merged into the one view.

### Alarm Actions
Spotlight Clients in the federation have access to all Alarm Action rules in the federation. The condition "The Diagnostic Server is…" is added to every pre-existing Alarm Action rule from the newly added Spotlight Diagnostic Server. Do nothing for Alarm Action rules specific to that Spotlight Diagnostic Server. For Alarm Action rules applicable to the federation, remove the condition "The Diagnostic Server is…" and delete duplicate rules.

### Planned Outages
Spotlight Clients in the federation have access to all scheduled planned outages for all Spotlight connections monitored in the federation.

### Configuration templates
Spotlight Clients in the federation have access to all configuration templates in the federation. The configuration templates from the newly joined Spotlight Diagnostic Server will be accessible to all Spotlight Clients in the federation. Any two templates with the same name will both be renamed to remain separate.

### Spotlight license
The Spotlight license applied to the Configuration server is applied to the federation. For more information, see Configuration server on page 11.


{% include links.html %}
