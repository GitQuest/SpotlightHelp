---
title: Install Spotlight Enterprise
tags: [setup]
keywords: setup, install
summary: "A minimal Spotlight Enterprise deployment consists of a Spotlight Diagnostic Server (to collect Spotlight data), a Spotlight Client (to view Spotlight data) and a Playback Database (to store recent history). These components are installed by the Spotlight Enterprise installer."
sidebar: p_enterprise_sidebar
permalink: enterprise_install.html
folder: SpotlightEnterprise
---


## Permissions required during installation

### The Windows user installing Spotlight
When installing the Spotlight Diagnostic Server, Windows administrator privileges are required to register the Spotlight Diagnostic Server as a Windows service and to create the Windows user groups that are used to authenticate Spotlight clients. When installing the Spotlight Diagnostic Server on a remote machine, the Windows account on the Spotlight client must have Windows administrator privileges on the Spotlight Diagnostic Server host. The local computer must be able to authenticate this user.

### Elevated privileges
In many cases, the Spotlight installer will run at elevated privileges in order to perform the required actions. These privileges can specifically be allowed or disallowed by system administrators by means of standard Microsoft Installer (MSI) policy settings. If the Spotlight Diagnostic Server user does not have privileges to start services, that privilege is granted by Spotlight during the installation process, if possible.

### Multiple users of a system
If multiple users of a system install Spotlight for use, the additional users must be local administrators.

## Run the Spotlight Enterprise installer

A minimal Spotlight Enterprise deployment consists of a Spotlight Diagnostic Server (to collect Spotlight data), a Spotlight Client (to view Spotlight data) and a Playback Database (to store recent history). These components are installed by the Spotlight Enterprise installer.

### System requirements

We only support installation on 64-bit systems, from Windows 7/2008 onwards.

### Welcome and select the type of install

Select **Compact** to install the Spotlight Client and Spotlight Diagnostic Server on the current computer.

Otherwise, select **Typical**.


Scenarios that may be involved with a typical install include:

* Install the Spotlight Diagnostic Server on a computer networked to the current computer.
* Install the Spotlight Client on the current computer to connect to a preexisting Spotlight Diagnostic Server.


### The Spotlight Client

The Spotlight Client will be installed as follows, unless you indicate otherwise

```
C:\Program Files (x86)\Dell\Spotlight on SQL Server
```

Do not install the Spotlight Client in the same location as an existing (but different entity of) Spotlight. If you install a different Spotlight after you have installed Spotlight Enterprise, do not install the new Spotlight in the Spotlight Enterprise directory.

### The Spotlight Diagnostic Server

#### Install location

Default installation folder for the Diagnostic Server:

```
C:\Program Files\Dell\Diagnostic Server
```

During a Typical install the diagnostic server can be installed remotely.

{% include tip.html content="Consider installing the Spotlight Diagnostic Server on a computer that is always switched on. Some Spotlight Diagnostic Server functionality requires Internet access." %}

#### Diagnostic Server Account

The Spotlight Diagnostic Server will run under this Windows account. Enter a domain user account or select the local system account. These credentials can later be used to authenticate Spotlight connections to monitor SQL Server instances and Windows Server.

#### Diagnostic Server Users

Spotlight uses the Spotlight diagnostic user groups to authenticate the Spotlight Client to the Spotlight Diagnostic Server, to authenticate a user's right to configure Spotlight and execute actions on monitored systems. The Windows user installing Spotlight (on the Spotlight Client) is automatically added to all Spotlight diagnostic user groups.

Add more users to the Spotlight diagnostic user groups if required. Members of these groups can be Windows users or Windows domain groups. Aliases are not supported.

#### Auto update Diagnostic Server

When **Selected** the Spotlight Diagnostic Server will receive minor updates (scripts and configuration) automatically. Ensure the Spotlight Diagnostic Server can access the Internet.

When **Not Selected** all updates to the Spotlight Diagnostic Server will require a new version and installation of Spotlight Enterprise.

### The Playback Database

The Spotlight installer installs the Playback Database following installation of the Spotlight Diagnostic Server. Every Spotlight Diagnostic Server connects to its own Playback Database. The Spotlight installer will ask you to provide the following information when it installs the Playback Database.

#### Instance

Select the SQL Server instance to install the Playback Database on. The Playback Database can be installed on the same Windows Server as the Spotlight Diagnostic Server or a different server dependent on the size of the deployment.

#### Authentication

Select Windows or SQL Server authentication.

#### Database

Optionally rename the database. The default name is **SpotlightPlaybackDatabase**. If the database has not already been created, click **Create** to create the database.



{% include links.html %}
