---
title: Spotlight Diagnostic Server
summary: "The Spotlight Diagnostic Server is at the core of the Spotlight Enterprise architecture. All Spotlight data passes through the Spotlight Diagnostic Server."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_ds.html
folder: SpotlightEnterprise
---

## Installation

The Spotlight Diagnostic Server is a Windows service. For specifications see the [Release Notes][enterprise_releasenotes_systemrequirements].

The Spotlight Diagnostic Server is installed by the [Spotlight installer][enterprise_install].

## Deployment

### View data and configure Spotlight

Configure the Spotlight Diagnostic Server from Spotlight Clients.

### Playback Database

Recent historical data is stored in the playback database. Each Spotlight Diagnostic Server requires its own Playback Database.

### Spotlight Statistics Repository

Enabling of the Spotlight Statistics Repository is optional. Many Spotlight Diagnostic Server can connect to the same Spotlight Statistics Repository.

### Monitored connections in the deployment

The Spotlight Diagnostic Server collects data from SQL Server, Windows and other supported connection types monitored by Spotlight.

A single Spotlight Diagnostic Server is designed to monitor a maximum of 100 SQL Servers, Analysis Services or Replication instances and 100 Windows servers. Exceeding this recommended limit on 32 bit environments may result in poor performance or product instability, due to the 1 Gb memory limit. On 64 bit environments theoretically more connections can be monitored as the 1 Gb limit no longer applies, however testing of this has been limited.

### Deployment over the Windows network

A Spotlight Enterprise deployment consists of many components that may be spread over a wide network. Spotlight's ability to function, to collect and display data, may depend on account permissions granted over the network and specific open network ports.

### Spotlight services requiring Internet access

The Spotlight Diagnostic Server requires access to the Internet when enabling Spotlight Cloud services.

### Account permissions

The Windows account that the Spotlight Diagnostic Server runs under could be a domain user account or the local system account. These credentials can be used to authenticate Spotlight connections to monitor SQL Server instances and Windows Server, and to connect the Spotlight Diagnostic Server to the Playback Database and Spotlight Statistics Repository.

### Federation

Most deployments of Spotlight have one Spotlight Diagnostic Server, however a deployment may consist of multiple Spotlight Diagnostic Server or a federation of Spotlight Diagnostic Server if the organization requires Spotlight to monitor more connections than a single Spotlight Diagnostic Server allows or the organization has setup geographic hubs. See [Federation of Spotlight Diagnostic Server][enterprise_backend_federation]


## Maintenance

### Backup Spotlight data

Spotlight configuration data is stored in the conf folder on the Spotlight Diagnostic Server. You can perform backups of the Spotlight configuration data by backing up this folder regularly.

### Start and stop the Spotlight Diagnostic Server

The Spotlight Diagnostic Server is a Windows service and can be started and stopped via the Windows Control Panel.



{% include links.html %}
