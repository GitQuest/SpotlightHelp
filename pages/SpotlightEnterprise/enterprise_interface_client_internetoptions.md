---
title: Internet Options on the Spotlight Client
summary: "The Spotlight Client connects to the Spotlight Diagnostic Server via Internet port 40403. If you have customized Internet Options on the Spotlight Client, verify that your customized configurations do not conflict with Spotlight."
sidebar: p_enterprise_sidebar
permalink: enterprise_interface_client_internetoptions.html
folder: SpotlightEnterprise
---

## Windows Control Panel \| Internet Options \| Advanced

On the computer hosting the Spotlight Client:

1. Open the **Control Panel \| Internet Options**.
2. Select the **Advanced** tab.
3. Verify **Use TLS 1.2** is selected.


{% include imageClient.html file="pane_windows_internetproperties_ssltls.png" alt="Internet Options" %}


## Verification

Verify the Spotlight Client can access the Spotlight Diagnostic Server via Internet port 40403.

Use a web browser to look up the following URL.

```
https://<ds-address>:40403/
```

Replace **\<ds-address\>** with the Spotlight Diagnostic Server host address. The display confirms HTTPS port 40403 is open.

If you still have problems, see also [Spotlight services requiring Internet access][enterprise_backend_ds_internetaccess].


{% include links.html %}
