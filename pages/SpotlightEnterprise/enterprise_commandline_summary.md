---
title: Windows Powershell / Command line access
summary: "Windows Powershell / Command line access requires the following."
sidebar: p_enterprise_sidebar
permalink: enterprise_commandline_summary.html
folder: SpotlightEnterprise
---


## Requirements
Microsoft Windows Powershell 3.0 or above is required. Older operating systems (for example Windows Server 2008 R2) require an upgrade of the Windows Management Framework in order to access Spotlight from the command line. [Download Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595)

For commands where user / password details are required ensure the user is a member of the [Spotlight Diagnostic User Groups](enterprise_backend_spotlightdiagnosticusergroups) **Spotlight Diagnostic Administrators** or **Spotlight Diagnostic Users**. Where there are multiple Spotlight Diagnostic Servers in a [federation](enterprise_backend_federation) the user is required to be a member of Spotlight Diagnostic Administrators or Spotlight Diagnostic Users for all Spotlight Diagnostic Servers in the federation.

## Access Spotlight from Windows Powershell / the command line

From Windows Powershell, enter command: **Import-DS | Add-DS -PassThru**.

{% include tip.html content="Enter command **get-dS** to verify the Spotlight Diagnostic Server has been imported correctly." %}

{% include tip.html content="In some special situations or for some platforms, if **Import-DS** does not work for you then open the **Console** directory in the Spotlight Client installation directory (usually C:\Program Files (x86)\Quest Software\Spotlight Enterprise). Right click the file **ds-cli.cmd** and select **Open** to open the command prompt." %}


## Command Spotlight from Windows Powershell / the command line

* Basic commands
* Windows Powershell / Command line parameters
* Add a list of connections
* Remove many connections
* Add a planned outage schedule
* Alarm commands
* Manage access to Spotlight connections


{% include links.html %}
