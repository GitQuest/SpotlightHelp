---
title: Federate Diagnostic Servers
summary: "The Spotlight Client is connected to a federated system if more than one Spotlight Diagnostic Server is listed on this screen. Use this dialog to manage the Spotlight Diagnostic Server in the federation."
sidebar: p_enterprise_sidebar
permalink: enterprise_cfgds_federate.html
id: 1011
folder: SpotlightEnterprise
---





## Open this screen from the Spotlight Client

1. Click **Configure \| Diagnostic Server**.
   {% include imageClient.html file="tb_config_dserver.png" alt="Configure Diagnostic Server" %}
2. Select **Federate Diagnostic Servers**


## List the Spotlight Diagnostic Server

List the Spotlight Diagnostic Server in the federated system. The Spotlight Client is connected to a federated system if more than one Spotlight Diagnostic Server is listed on this screen.

### Host

The Windows host of the Spotlight Diagnostic Server.

### Connection Status

The current real-time status of the Spotlight Diagnostic Server.

### Connections

The number of Spotlight connections monitored by this Spotlight Diagnostic Server.  Add the number of Spotlight connections monitored by each Spotlight Diagnostic Server to determine the number of Spotlight connections monitored by the Federation.

### Configuration Server

One Spotlight Diagnostic Server in the federation selected as the Configuration server.

Configuration shared between the Spotlight Diagnostic Server in the federation is applied to the Configuration server. Other Spotlight Diagnostic Server in the federation poll the Configuration server for updates..

Spotlight Diagnostic Server in the federation authenticate with the Configuration server using Windows authentication over TCP Port 40403. For each Spotlight Diagnostic Server in the federation, the Windows account that the Spotlight Diagnostic Server is running under must be valid in the domain of the Configuration server.

The Configuration server should have a reliable and fast Internet connection to each of the other Spotlight Diagnostic Server in the federation.



## Add Spotlight Diagnostic Server

Add a Spotlight Diagnostic Server to the federation. The Spotlight Diagnostic Server to add should be installed and operational and accessible to the Spotlight Client.

1. Click **Add** to add the Spotlight Diagnostic Server to the federation.
2. From the dialog that opens, select the host of the Spotlight Diagnostic Server to add to the federation.


Note:

* A Spotlight Diagnostic Server can connect to one federation at a time. Remove a Spotlight Diagnostic Server from one federation before adding it to a different federation.
* The Spotlight Diagnostic Servers in a federation cannot monitor the same connections. Federation cannot proceed where duplicate connections exist. Spotlight will prompt you to delete duplicate connections.
* Windows connections that have the same VMware host connection can only be monitored by one Spotlight Diagnostic Server in a federation because the VMware host connection
can only defined in one Spotlight Diagnostic Server and connections in one Spotlight Diagnostic Server cannot use a host connection
from another Spotlight Diagnostic Server. A workaround for this restriction is to create duplicate VMware host connections in different Diagnostic Servers by using an IP address or fully qualified host name.        
* Each Spotlight Diagnostic Server in the federation must be running the same Spotlight version. Federation is supported for Spotlight Enterprise (Spotlight on SQL Server) versions 11.6 and above.
* Each Spotlight Diagnostic Server in the federation authenticates with one selected Spotlight Diagnostic Server in the federation (the Configuration server documented on the [Configure Operations][enterprise_backend_federation_cfgops] page). Each Spotlight Diagnostic Server authenticates with the Configuration server using Windows authentication over TCP port 40403. The Windows account that each Spotlight Diagnostic Server is running under must be valid in the domain of the Configuration server. Spotlight Diagnostic Server running under the built in Windows accounts (local system or network service) cannot be federated.
* All Spotlight Clients in the federation retrieve monitoring information directly from the Spotlight Diagnostic Server. TCP port 3843 must be open for incoming connections from all Spotlight Diagnostic Server in the federation.
* We recommend implementing a VPN with a federated system for increased security.
* Connections that have been migrated from one Spotlight Diagnostic Server to another within a federation do not have their Playback and Spotlight Statistics Repository data preserved automatically. If you want to preserve that data see [Reorganizing SSR historical data after creating a federation](enterprise_backend_federation_add.html#reorganizingssr) .

### On adding a Spotlight Diagnostic Server to the federation

#### Monitored connections

The Spotlight Clients connected to the Spotlight Diagnostic Server that has been added to the federation now connect to the federation of Spotlight Diagnostic Server. Spotlight Clients in the federation monitor connections from all Spotlight Diagnostic Server in the federation.

Data to / from monitored connections is communicated directly from Spotlight Diagnostic Server to Spotlight Client. It is required that all Spotlight Clients have open communications with all Spotlight Diagnostic Server in the federation.

#### Custom views

Spotlight Clients in the federation have access to all custom views in the federation. The custom views from the newly joined Spotlight Diagnostic Server will be accessible to all Spotlight Clients in the federation. Any two custom views with the same name will be merged into the one view.

#### Configure \| Alarm Actions

Spotlight Clients in the federation have access to all Alarm Action rules in the federation. The condition "The Diagnostic Server is…" is added to every pre-existing Alarm Action rule from the newly added Spotlight Diagnostic Server. Do nothing for Alarm Action rules specific to that Spotlight Diagnostic Server. For Alarm Action rules applicable to the federation, remove the condition "The Diagnostic Server is…" and delete duplicate rules.

#### Configure \| Planned Outage

Spotlight Clients in the federation have access to all scheduled planned outages for all Spotlight connections monitored in the federation.

#### Configuration templates

Spotlight Clients in the federation have access to all configuration templates in the federation. The configuration templates from the newly joined Spotlight Diagnostic Server will be accessible to all Spotlight Clients in the federation. Any two templates with the same name will both be renamed to remain separate.

#### Spotlight license

The Spotlight license applied to the Configuration server is applied to the federation.

## Set as Configuration server

One Spotlight Diagnostic Server in the federation is selected as the Configuration Diagnostic Server.

Configuration shared between the Spotlight Diagnostic Server in the federation is applied to the Configuration server. Other Spotlight Diagnostic Server in the federation poll the Configuration server for updates.

The Configuration server should have a reliable and fast Internet connection to each of the other Spotlight Diagnostic Server in the federation.

## Remove Spotlight Diagnostic Server

To remove a Spotlight Diagnostic Server from the federation:

1. Select the Spotlight Diagnostic Server from the list.
2. Click **Remove** to remove the Spotlight Diagnostic Server from the federation.
3. Confirm your request to remove the Spotlight Diagnostic Server.

### The federation now a Spotlight Diagnostic Server has been removed

#### Monitored connections

Spotlight Clients connected to the federation can no longer monitor connections from the removed Spotlight Diagnostic Server.

Spotlight Clients with the removed Spotlight Diagnostic Server as their primary server are no longer connected to the federation.

#### Custom views

The Custom Views in the federation no longer show monitored connections from the removed Spotlight Diagnostic Server.

#### Configure \| Alarm Actions

All Alarm Actions with condition "Where the Diagnostic Server is…" the removed Spotlight Diagnostic Server are removed from the federation.

#### Configure \| Planned Outage

Planned Outages for the federation no longer show monitored connections from the removed Spotlight Diagnostic Server.

#### Configuration templates

All Configuration templates remain available to the federation.

#### Spotlight license

The Spotlight license for the federation does not change. Note that if the Configuration server is removed from the federation the Spotlight license does change to the license of the federation's new Configuration server.


### The deployment of a Spotlight Diagnostic Server that has been removed from the federation


#### Monitored connections

Spotlight Clients with the removed Spotlight Diagnostic Server as their primary server are no longer connected to the federation. They monitor connections directly from the Spotlight Diagnostic Server.

#### Custom views

Any Spotlight Client connecting to the Spotlight Diagnostic Server will have access to all Custom Views from the federation. The Custom Views show only connections monitored directly from the Spotlight Diagnostic Server.

#### Configure \| Alarm Actions

Alarm Actions with condition "Where the Diagnostic Server is…" the removed Spotlight Diagnostic Server are available to the Spotlight Diagnostic Server when it is removed from the federation. Alarm Actions from the federation that do not have the condition "Where the Diagnostic Server is…" are also available to the Spotlight Diagnostic Server when it is removed from the federation.

#### Configure \| Planned Outage

Any Spotlight Client connecting to the Spotlight Diagnostic Server will have access to all Planned Outages on connections monitored by that Spotlight Diagnostic Server.

#### Configuration templates

The configuration templates from the federation remain accessible to the Spotlight Diagnostic Server after it has been removed from the federation.

#### Spotlight license

The Spotlight Diagnostic Server takes on the Spotlight license that was given to it when it joined the federation; that is the Spotlight license applied to the Configuration server at the time the Spotlight Diagnostic Server joined the federation.


{% include links.html %}
