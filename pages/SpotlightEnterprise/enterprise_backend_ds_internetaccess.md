---
title: Spotlight services requiring Internet access
summary: "Use this page to ensure the Spotlight Diagnostic Server is appropriately configured for Internet access."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_ds_internetaccess.html
folder: SpotlightEnterprise
---


## The following Spotlight services require Internet access on the Spotlight Diagnostic Server.

### Configure uploading to Spotlight Cloud

Monitor Spotlight connections in a web browser or Spotlight Cloud Mobile. Upload performance data for health check analysis. See [Upload to the Spotlight Cloud][enterprise_cfgds_spotlightcloud].


## How to ensure the Spotlight Diagnostic Server is appropriately configured to access the Internet

### Windows Control Panel \| Internet Options \| Connections

On the computer hosting the Spotlight Diagnostic Server:

1. Open the **Control Panel \| Internet Options**.
2. Select the **Connections** tab.
3. Click **LAN Settings**.
4. Ensure the settings on this screen are appropriate to the settings of your local environment.

{% include note.html content="After the Spotlight Diagnostic Server is installed, [restart the Spotlight Diagnostic Server][enterprise_backend_ds_startstop] after changes are made." %}

### Windows Control Panel \| Internet Options \| Advanced

On the computer hosting the Spotlight Diagnostic Server:

1. Open the **Control Panel \| Internet Options**.
2. Select the **Advanced** tab.
3. Ensure Use HTTP 1.1 and Use HTTP 1.1 through proxy connections are selected.

{% include imageClient.html file="pane_windows_internetproperties.png" alt="Internet Properties" %}

{% include note.html content="After the Spotlight Diagnostic Server is installed, [restart the Spotlight Diagnostic Server][enterprise_backend_ds_startstop] after changes are made." %}


## Internet URLs - Spotlight Cloud

Spotlight Cloud requires incoming and outgoing HTTPS connections to the following URLs. To verify access to the Spotlight Cloud, open a web browser on the Spotlight Diagnostic Server host and look up these URLs.

URL | Web browser lookup
----|-------------------
https://www.spotlightessentials.com | Successful display of the Spotlight Cloud web site confirms HTTPS port 443 is open.
https://api.spotlightessentials.com | Successful display of the text “Welcome to Spotlight Web API!” confirms access for uploading.


{% include links.html %}
