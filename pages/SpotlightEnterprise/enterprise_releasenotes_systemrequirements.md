---
title: System Requirements
keywords: release notes
summary: "Before installing Spotlight Enterprise, ensure that your system meets the following minimum hardware and software requirements."
sidebar: p_enterprise_sidebar
permalink: enterprise_releasenotes_systemrequirements.html
folder: SpotlightEnterprise
---


## Client requirements

### Platform
1 GHz Pentium® 4 PC

### Memory
1 GB RAM

### Hard disk space
200 MB

This space should exist on a local disk drive rather than a network drive.

### Operating system

* Microsoft® Windows 10 (64-bit)
* Microsoft Windows 8.1 (64-bit)
* Microsoft Windows 8 (64-bit)
* Microsoft Windows 7 (64-bit)
* Microsoft Windows Server 2016 (64-bit)
* Microsoft Windows Server 2012 R2 (64-bit)
* Microsoft Windows Server 2012 (64-bit)
* Microsoft Windows Server 2008 R2 (64-bit)
* Microsoft Windows Server 2008 (64-bit)

### Screen resolution
Minimum Resolution: 1280x1024

DPI scaling is supported for large fonts, Windows 8.1 and above.

### CD-ROM drive or Internet connection
This is required for installation only.

### Additional software requirements

#### SQL Server Client Tools
Required to use the Discovery Wizard to locate SQL Servers on your network. SQL Server Client Tools can be found on the Microsoft SQL Server installation media.
Client Connectivity Tools - Required to monitor an Analysis Services server.

#### .NET
It is recommended that the latest .NET be installed.
Minimum .NET 4.5.
.NET is required for the Performance Health drilldowns and the Spotlight Report Viewer.

#### Microsoft Internet Explorer® 6.0 or later.

#### Microsoft Data Access Components (MDAC)
MDAC includes the ODBC and other components that enable a connection to be established to a SQL Server database. The database may be local or remote. Your client machine must have MDAC 2.7 (or later) installed.

MDAC is available from the Microsoft website: www.microsoft.com/downloads

To find out the version of MDAC that you are currently running, you can download an application from the Microsoft website called the Component Checker Tool. Review the following Microsoft Knowledge Base article for more information: http://support.microsoft.com/kb/301202

#### Microsoft Windows Powershell 3.0 or above
Microsoft Windows Powershell 3.0 or above is required to [access Spotlight from the command line][enterprise_connect_commandline].


## Spotlight Diagnostic Server requirements

### Platform
2 GHz Pentium Dual Core

### Memory
2 GB RAM

### Hard disk space
300 MB

If the Diagnostic Server’s connection to the Spotlight Statistics Repository or Playback database is interrupted, the Diagnostic Server will cache data to the local disk. In this event, an extra 2 MB per hour, per monitored server is required.

### Operating system

* Microsoft Windows 10 (64-bit)
* Microsoft Windows 8.1 (64-bit)
* Microsoft Windows 8 (64-bit)
* Microsoft Windows 7 (64-bit)
* Microsoft Windows Server 2016 (64-bit)
* Microsoft Windows Server 2012 R2 (64-bit)
* Microsoft Windows Server 2012 (64-bit)
* Microsoft Windows Server 2008 R2 (64-bit)
* Microsoft Windows Server 2008 (64-bit)

{% include tip.html content="The Diagnostic Server is not supported on a cluster or High Availability Always On." %}


### .NET
.NET 4.5 or later.


### Virtualized Environments

We support deploying Spotlight Entrprise in a virtualized environment.

### Additional requirements

#### SQL Server Client Tools
Required to use the Discovery Wizard to locate SQL Servers on your network. SQL Server Client Tools can be found on the Microsoft SQL Server installation media.
Client Connectivity Tools - Required to monitor an Analysis Services server.

#### SQL Server Management Tools
Required to monitor an Analysis Services server, a SQL Server Replication environment, and the use of Session Trace when monitoring a SQL Server.

The SQL Server Management Tools are available from any SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014 or SQL Server 2016 edition except SQL Server Express and SQL Server Compact. The version required corresponds to the latest version of SQL Server that you are monitoring. If you are monitoring SQL Server 2000 servers, you need the Management Tools from SQL Server 2005.

#### Internet Access
Required by Auto Update and Spotlight Cloud. Required to monitor your Spotlight connections from the Spotlight web site or a mobile device.

#### Connection Limit
A single Spotlight Diagnostic Server is designed to monitor a maximum of 100 SQL Servers, Analysis Services or Replication instances and 100 Windows servers. Exceeding this recommended limit on 32 bit environments may result in poor performance or product instability, due to the 1 Gb memory limit. On 64 bit environments theoretically more connections can be monitored as the 1 Gb limit no longer applies, however testing of this has been limited. In environments that exceed this number of connections, consider a deployment of federation of Spotlight Diagnostic Server.


## Monitoring
Spotlight Enterprise is able to monitor the following connections

### Databases
Spotlight can be used to monitor:

* [SQL Server][sqlserver_connect_requirements]
* SQL Server Analysis Services
* SQL Server Availability Group
* SQL Server Replication

### Database Cloud Service
Spotlight can be used to monitor SQL Azure.

### Operating Systems
Spotlight can be used to monitor:

* [Microsoft Windows][windows_connect_requirements]
* [Unix/Linux][unix_connect_requirements]

### Virtualization
Spotlight can monitor virtual environments and virtual guest machines in a virtual environment.

* [VMware® ESX infrastructure.][vmware_connect_requirements]
* [Hyper-V® 6.2 and above.][hyperv_connect_requirements]


## Playback database requirements

### Database sizing
The MS Model database is used. The database size usually starts at about 3MB (data size) and 1MB (log size).

### Hard disk space
Requires approximately 270 MB for each monitored SQL Server instance and the corresponding monitored Windows host on which the SQL Server instance resides. Retains 7 days of historical data for each connection in the Playback Database by default. This is configurable.

This estimate assumes default configuration in an average environment. Actual space used will depend on your environment and any data collection/storage configuration changes that are made. For more information, see the Spotlight Enterprise Sizing Wizard. You can access the wizard from the Spotlight Installation Center.

### SQL Server

The Playback Database can be installed on:

* SQL Server 2016
* SQL Server 2014
* SQL Server 2012
* SQL Server 2008 R2
* SQL Server 2008
* SQL Server 2005

{% include tip.html content="Due to the size of the Playback Database, it is recommended that this database is not installed on a SQL Express instance. The Playback Database is not supported on High Availability Always On and mirrored databases. The Playback Database cannot be installed on SQL Server 2000." %}


### Other requirements
The SQL Browser service must be running on the machine where the Playback Database is installed. Alternatively you can use the host and port number of the (named) SQL Server instance you want to connect to, when creating a connection and connecting to the Playback Database.

### Maintenance
The Diagnostic Server runs maintenance procedures daily at 3am for the Playback Database. This is configurable.

It is highly recommended that regular maintenance is performed on the Playback Database. See [Maintenance plan for Spotlight Statistics Repository and Playback Database][enterprise_backend_maintenanceplan].

## Spotlight Statistics Repository Requirements

### Database sizing
The MS Model database is used. The database size usually starts at about 3MB (data size) and 1MB (log size).

### Hard Disk Space
Approximately 1.2 GB for each monitored SQL Server instance and the corresponding monitored Windows host on which the SQL Server instance resides.
This estimate assumes default configuration in an average environment. Actual space used will depend on your environment and any data collection/storage configuration changes that are made. For more information, see the Spotlight Enterprise Sizing Wizard. You can access the wizard from the Spotlight Installation Center.

### SQL Server
The Spotlight Statistics Repository can be installed on:

* SQL Server 2016
* SQL Server 2014
* SQL Server 2012
* SQL Server 2008 R2
* SQL Server 2008
* SQL Server 2005

{% include tip.html content="Due to the size of the Spotlight Statistics Repository, it is recommended that this database is not installed on a SQL Express instance. The Spotlight Statistics Repository is not supported on High Availability Always On and mirrored databases. The Spotlight Statistics Repository cannot be installed on SQL Server 2000." %}


### Other Requirements
The SQL Browser service must be running on the machine where the Spotlight Statistics Repository is installed. Alternatively you can use the host and port number of the (named) SQL Server instance you want to connect to, when creating a connection and connecting to the Spotlight Statistics Repository.

The TCP protocol must be enabled on the instance where the Spotlight Statistics Repository resides.

### Maintenance
It is highly recommended that regular maintenance is performed on the Spotlight Statistics Repository. See [Maintenance plan for Spotlight Statistics Repository and Playback Database][enterprise_backend_maintenanceplan].


## Upgrade and compatibility
Use the Spotlight installer to upgrade from Spotlight on SQL Server version 10.0 or later. To upgrade from an earlier version of Spotlight than 10.0, upgrade to at least version 10.0 before upgrading to 11.7. To upgrade from 10.5.0, first upgrade to 10.5.2 and then upgrade to 12.0.

### Spotlight Diagnostic Server - upgrade
The following is transferred during the upgrade:

* Connection properties for all monitored servers (including changes to scheduling and alarms)
* Enterprise views
* Collector properties
* Alarm Actions (These include running a program and sending an email.)
* Planned Outages
* Global options such as user-created Error Log rules
* Configuration information for the Spotlight Statistics Repository (applicable to deployments that include the Spotlight Statistics Repository.)

### Alarms requiring acknowledgment - upgrade
The Spotlight factory settings for alarms requiring acknowledgment changes on upgrade from Spotlight 11.2. Only Connection Failure alarms are now factory set to require acknowledgment.

The alarms that were factory set to require acknowledgment in Spotlight 11.2 are as follows. They are included here so you can choose to manually enable them to require acknowledgment again post upgrade if required.

* Availability Group - Failed Over
* Clusters - Failed over
* Diagnostic Server - Auto Update Success
* Error Log - Error Count
* LiteSpeed Backup Failed
* LiteSpeed Backup Warning
* Locks - Blocked Processes
* Locks - Deadlocks
* Mirroring Failedover
* SQL Agent - Jobs Failed

### Monitoring your Spotlight connections on a mobile device - upgrade
If you are upgrading from Spotlight on SQL Server 11.1.x and used that version or earlier to monitor your Spotlight on SQL Server connections on a mobile device and intend to continue monitoring your connections on a mobile device then the following additional upgrade instructions are required.

1. Uninstall the Spotlight Web Publisher via **Windows \| Control Panel \| Programs and Features**. The Spotlight Web Publisher was required in the past to monitor SQL Server connections on a mobile device. It is now important that you uninstall it. By default the Spotlight Web Publisher was installed on the same computer as the Spotlight Diagnostic Server.
2. From the Spotlight Client, click **Configure \| Spotlight Cloud**. Select **Upload data to Spotlight Cloud**. Ensure your Spotlight Cloud (Spotlight Essentials) account details are correct.

{% include links.html %}
