---
title: Network ports
summary: "Spotlight's ability to function, to collect and display data, may depend on account permissions granted over the network and specific open network ports."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_networkports.html
folder: SpotlightEnterprise
---

## Network ports on the Spotlight Diagnostic Server

### TCP 3843

This port is used by the Spotlight Client to communicate with the Spotlight Diagnostic Server. This port must be open for incoming connections on the Spotlight Diagnostic Server host.


### TCP 3166

This port is used by the Spotlight Diagnostic Server to communicate with the Spotlight OOP Collector process on the same host. No external connections are required on this port.


### TCP 443

This port is used by the Spotlight Diagnostic Server to communicate with Spotlight Cloud. This port must be open for outgoing connections on the Spotlight Diagnostic Server host when uploading to Spotlight Cloud is enabled on the Spotlight Diagnostic Server.


### TCP 40403

This port is used by the Spotlight Client to communicate with the Spotlight Diagnostic Server. This port must be open for incoming connections on the Spotlight Diagnostic Server host.


## Network ports on the Spotlight Cloud Diagnostic Server

### TCP 3166

This port is used by the Spotlight Cloud Diagnostic Server to communicate with the Spotlight Native Collector process on the same host. No external connections are required on this port.


### TCP 443

This port is used by the Spotlight Cloud Diagnostic Server to communicate with Spotlight Cloud. This port must be open for outgoing connections on the Spotlight Cloud Diagnostic Server host.


### TCP 8930 and 7985

These two ports are used on the Spotlight Cloud Diagnostic Server host for internal communications between the Spotlight Cloud Diagnostic Server service and the Spotlight Cloud Diagnostic Server App.


## Network ports on monitored Windows servers and hosts of database connections

### TCP 135
The Spotlight Diagnostic Server uses WMI queries to retrieve performance counter information from monitored Windows Server and hosts of database connections. Verify TCP port 135 is open on monitored Windows server and hosts of database connections.

### UDP 1434
SQL Server uses UDP 1434 to locate the SQL Server instance port number. If UDP 1434 is closed then the SQL Server instance port number must be included in the connection string used to connect Spotlight to the SQL Server instance.


## Network ports on monitored Unix/Linux servers and hosts of database connections

### SSH
Verify the port number for SSH (secure shell) connection to the Unix/Linux machine is open. The default port number is 22.


## Checks to verify ports are open
* Verify a firewall is not blocking port traffic.
* Verify no other service is using the port.
* Verify the port is not configured as an ephemeral port. This issue may arise if you have configured your Windows ports beyond Windows Factory settings or your Windows host is Windows 2008 with Exchange Server 2007. For more information on ephemeral (dynamic) ports, see [https://support.microsoft.com/en-us/kb/929851](https://support.microsoft.com/en-us/kb/929851)


{% include links.html %}
