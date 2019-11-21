---
title: Configure operations
summary: "Any Spotlight Client in the federation can configure the operations of any Spotlight Diagnostic Server in the federation. Any Spotlight Client in the federation can configure the operations of the federation."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_federation_cfgops.html
folder: SpotlightEnterprise
---

## Use a Spotlight Client to configure operations

Any Spotlight Client in the federation can configure the operations of any Spotlight Diagnostic Server in the federation.

1. Open the Spotlight Client.
2. Click **Configure \| Diagnostic Server**.
3. Select the Spotlight Diagnostic Server operation to configure (Database maintenance schedule - Use of Extended Events).
4. The dialog to configure the selected Spotlight Diagnostic Server operation opens. Select the Spotlight Diagnostic Server and set the new configuration.

Any Spotlight Client in the federation can configure the operations of the federation.

1. Open the Spotlight Client.
2. Click **Configure \| Diagnostic Server \| Federate Diagnostic Servers**.
3. Add / Remove Spotlight Diagnostic Server from the federation and set the Configuration server.

   {% include imageClient.html file="pane_ds_federatediagnosticservers.png" alt="Federate Diagnostic Servers" %}

## Configuration server
One Spotlight Diagnostic Server in the federation is selected as the Configuration server.

Configurations shared between the Spotlight Diagnostic Server in the federation are applied to the Configuration server. Other Spotlight Diagnostic Server in the federation poll the Configuration server for updates.

{% include imageClient.html file="figure_federation_Configuration-DS.png" alt="Configuration server" %}

The following configurations are applied directly from the Spotlight Client to the Configuration server. Other Spotlight Diagnostic Server in the federation poll for updates from the Configuration server.

* Custom views
* Configured Alarm Actions
* Planned Outages
* Configuration templates

{% include note.html content="If the Configuration server is down then any changes made by a Spotlight Client to any of the above configurations will not be saved. If any other Spotlight Diagnostic Server in the federation is offline then when it is online again it will poll to receive updates from the Configuration server. The Configuration server keeps transactions (recording changes to the above configurations) for 5 days." %}

### Steps to assign the Configuration server

1. Open a Spotlight Client in the federation.
2. From the Spotlight Client, click **Configure \| Diagnostic Server \| Federate Diagnostic Servers**.
3. Select the Spotlight Diagnostic Server.
4. Click **Set as Configuration server**.

Spotlight Diagnostic Server authenticate with the Configuration server using Windows authentication over TCP Port 40403. For each Spotlight Diagnostic Server in the federation, the Windows account that the Spotlight Diagnostic Server is running under must be valid in the domain of the Configuration server.

The Configuration server should have a reliable and fast Internet connection to each of the other Spotlight Diagnostic Server in the federation.

## Spotlight Clients and the primary server
Connect a Spotlight Client to a federation by connecting the Spotlight Client to any Spotlight Diagnostic Server in the federation. This is the primary server for the Spotlight Client.

Connect a Spotlight Client to a federation

1. Click **Configure \| Diagnostic Server**.
2. Click **Select a Diagnostic Server**
3. In the **Host** field type or select the machine name where the Spotlight Diagnostic Server is installed.

    {% include imageClient.html file="pane_ds_selectads.png" alt="Select a Diagnostic Server" %}


## Federation and playback data
In a federation of Spotlight Diagnostic Servers, each Spotlight Diagnostic Server connects to its own Playback Database.

{% include imageClient.html file="figure_federation_Federation-of-DS-and-playback.png" alt="Federation and playback data" %}

## Federation and the Spotlight Cloud
In a federation of Spotlight Diagnostic Server each Spotlight Diagnostic Server is independently configured for Spotlight Cloud.

{% include imageClient.html file="figure_federation_Federation-and-Cloud.png" alt="Federation and the Spotlight Cloud" %}

{% include links.html %}
