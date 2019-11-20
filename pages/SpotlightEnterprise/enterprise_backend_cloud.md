---
title: Spotlight Cloud
summary: "Health performance data can be uploaded to the Spotlight Cloud."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_cloud.html
folder: SpotlightEnterprise
---




## Configuration

The Spotlight Diagnostic Server must be configured to allow upload of data to the Spotlight Cloud. Use the Spotlight Client to [Confiure uploading to the Spotlight Cloud][enterprise_cfgds_spotlightcloud].

## Use

To retrieve the analysis of this data, use a web browser to sign in with your Quest account to [www.spotlightcloud.io](https://www.spotlightcloud.io).

## Data handling and Security

### What data are we uploading?
Spotlight on SQL Server Enterprise user can opt-in to send system configuration and performance metrics from SQL Server to SpotlightCloud.io. Data is collected and then sent periodically. Once it is uploaded we store it for analysis and consumption by the end user. From the data and subsequent analysis SpotlightCloud.io is able to generate a picture of your system's health and performance. 

### How is customer data transferred from Spotlight on SQL Server Enterprise to Cloud Connect?
When data is uploaded to cloud Connect it is sent via https to a cloud-based service running in Microsoft Azure. The low-level security protocols utilized during the data-transfer will depend on the client and the server.

### Where is customer data stored?
As of April 2018, all data is uploaded to Azure datacenters in North America. The datacenters utilized include: *North Central*, *South Central* and *East US2*.

The best place to go is the [Windows Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/) site itself.

### How long is customer data kept?
Data uploaded to Cloud Connect is kept indefinitely. However, we make no promises about how long we'll keep customers' data. Quest may purge 'old data' in order to keep our financial costs under control.

### How does Quest obfuscate Personally Identifiable Information (PII)?
SQL Statements and Query Plans are the only potention PII data in Spotlight on SQL Server Enterprise. They are not uploaded to Spotlight Cloud.

### How are users authenticated on the Spotlight on SQL Server Enterprise?

* Standards based authentication protocol OIDC.
* Claim based secured and signed authentication token.

### Where can I find security and compliance information on the Windows Azure Platform?
The best place to go is the [Windows Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/) site itself.

### Upload to Cloud issue Knowledge Base
INTERNAL - Spotlight Cloud error: "An existing connection was forcibly closed by the remote host"
The solution can be found here [KB 248894](https://supportadmin.prod.quest.corp/KBViewer/get/1-4XZUA91)

{% include links.html %}
