---
title: Install Spotlight Enterprise
summary: "The Spotlight Enterprise installer installs a Spotlight Diagnostic Server (to collect Spotlight data), a Spotlight Client (to view Spotlight data) and a Playback Database (to store recent history). These three elements constitute a minimal Spotlight Enterprise deployment which can be expanded post install."
sidebar: p_enterprise_sidebar
permalink: enterprise_install.html
folder: SpotlightEnterprise
---


## The size and shape of the deployment

In a small deployment the Spotlight Diagnostic Server, Spotlight Client and Playback Database can all be installed on the same host, however they don't have to be.

### Spotlight Clients

Run the Spotlight Enterprise installer on each computer where you want to install a Spotlight Client. Many Spotlight Clients can connect to one Spotlight Diagnostic Server. The Spotlight Enterprise installer can install the Spotlight Diagnostic Server remotely.


### Spotlight Diagnostic Server

Consider installing the Spotlight Diagnostic Server on a computer that is always switched on. Some Spotlight Diagnostic Server functionality requires Internet access. For example, where a Spotlight Diagnostic Server has access to the Internet, connections can be monitored from a web browser or a mobile device.

Where there are a large number of connections to be monitored or those connections are geographically widespread it may be appropriate to deploy multiple Spotlight Diagnostic Server where many Spotlight Clients monitor many connections through many Spotlight Diagnostic Server.

{% include tip.html content="Do not install multiple Spotlight Diagnostic Server on the same host. For example, customers of Spotlight Enterprise should not install the Spotlight Cloud Diagnostic Server and Spotlight Enterprise Diagnostic Sever on the same host." %}

### Playback Database

The Playback Database can be installed on the same host as the Spotlight Diagnostic Server, dependent on the number of SQL Server instances to be monitored.

### Windows network

Spotlight Clients, Spotlight Diagnostic Server, Playback Database and monitored connections communicate over a Windows network. Appropriate permissions ensure communications flow. For more information on these considerations see [Backend deployment][enterprise_backend].


### Factor in how many SQL Server instances you intend to monitor

#### 1 - 25 SQL Server instances
The Spotlight Diagnostic Server, Playback Database (and later the Spotlight Statistics Repository) can all be installed on the same host, as long as that host meets the minimum hardware requirements listed in the [release notes][enterprise_releasenotes_systemrequirements].

#### More than 25 SQL Server instances
It is recommended that the Playback Database (and later the Spotlight Statistics Repository) be hosted on a different server than the Spotlight Diagnostic Server host. The host for the Playback Database and Spotlight Statistics Repository should be configured with an appropriate amount of I/O bandwidth to meet demand. If your environment uses a storage area network (SAN) it may be possible to install the Spotlight Statistics Repository and the Playback Database on the same host.

#### Lots of SQL Server instances
Consider a deployment of more than one Spotlight Diagnostic Server. A single Spotlight Diagnostic Server is designed to monitor a maximum of 100 SQL Servers, Analysis Services or Replication instances and 100 Windows servers. Exceeding this recommended limit on 32 bit environments may result in poor performance or product instability, due to the 1 Gb memory limit. On 64 bit environments theoretically more connections can be monitored as the 1 Gb limit no longer applies, however testing of this has been limited. For more information on deployments with more than one Spotlight Diagnostic Server, see the [Federation][enterprise_backend_federation] page.



## Permissions required during installation

### The Windows user installing Spotlight
When installing the Spotlight Diagnostic Server, Windows administrator privileges are required to register the Spotlight Diagnostic Server as a Windows service and to create the Windows user groups that are used to authenticate Spotlight clients. When installing the Spotlight Diagnostic Server on a remote machine, the Windows account on the Spotlight client must have Windows administrator privileges on the Spotlight Diagnostic Server host. The local computer must be able to authenticate this user.

### Elevated privileges
In many cases, the Spotlight installer will run at elevated privileges in order to perform the required actions. These privileges can specifically be allowed or disallowed by system administrators by means of standard Microsoft Installer (MSI) policy settings. If the Spotlight Diagnostic Server user does not have privileges to start services, that privilege is granted by Spotlight during the installation process, if possible.

### Multiple users of a system
If multiple users of a system install Spotlight for use, the additional users must be local administrators.

## Run the Spotlight Enterprise installer

During installation you will be prompted to supply details for the Spotlight Diagnostic Server (to collect Spotlight data), Spotlight Client (to view Spotlight data) and Playback Database (to store recent history).

### Welcome and select the type of install

Select **Compact** to install the Spotlight Client and Spotlight Diagnostic Server on the current computer.

Otherwise, select **Typical**.


Scenarios that may be involved with a typical install include:

* Install the Spotlight Diagnostic Server on a computer networked to the current computer.
* Install the Spotlight Client on the current computer to connect to a preexisting Spotlight Diagnostic Server.


### The Spotlight Client

The Spotlight Client will be installed as follows, unless you indicate otherwise

```
C:\Program Files (x86)\Quest Software\Spotlight Enterprise
```

Do not install the Spotlight Client in the same location as an existing (but different entity of) Spotlight. If you install a different Spotlight after you have installed Spotlight Enterprise, do not install the new Spotlight in the Spotlight Enterprise directory.

### The Spotlight Diagnostic Server

#### Install location

Default installation folder for the Diagnostic Server:

```
C:\Program Files\Quest Software\Diagnostic Server
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
