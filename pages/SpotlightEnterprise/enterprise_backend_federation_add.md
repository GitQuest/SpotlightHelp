---
title: Make (add to) a federation
summary: "To make a federation, start with two separate Spotlight Diagnostic Server deployments. More Spotlight Diagnostic Server deployments can now be added to the federation."
sidebar: p_enterprise_sidebar
permalink: enterprise_backend_federation_add.html
folder: SpotlightEnterprise
---

Start with two separate Spotlight deployments.

{% include imageClient.html file="figure_federation_deployment-Project-0A-and-0B.png" %}

## Notes on making a federation

* A Spotlight Diagnostic Server can connect to one federation at a time. Remove a Spotlight Diagnostic Server from one federation before adding it to a different federation.
* The Spotlight Diagnostic Servers in the federation cannot be monitoring the same connections. Where duplicate connections exist, federation cannot proceed. Spotlight will prompt you to delete duplicate connections.
* Each Spotlight Diagnostic Server in the federation must be running the same Spotlight version. Federation is supported for Spotlight Enterprise (Spotlight on SQL Server) versions 11.6 and above.
* Each Spotlight Diagnostic Server in the federation authenticates with one selected Spotlight Diagnostic Server in the federation (the Configuration server documented on the [Configure Operations][enterprise_backend_federation_cfgops] page). Each Spotlight Diagnostic Server authenticates with the Configuration server using Windows authentication over TCP port 40403. The Windows account that each Spotlight Diagnostic Server is running under must be valid in the domain of the Configuration server. Spotlight Diagnostic Server running under the built in Windows accounts (local system or network service) cannot be federated.
* All Spotlight Clients in the federation retrieve monitoring information directly from the Spotlight Diagnostic Server. TCP port 3843 must be open for incoming connections from all Spotlight Diagnostic Server in the federation.
* We suggest that a VPN is implemented with a federated system for increased security.

## Steps to make (add to) a federation

1. Open a Spotlight Client.

   If the federation already exists, open any Spotlight Client connected to the federation. When federating two separate Spotlight Diagnostic Server, open a Spotlight Client connected to either Spotlight Diagnostic Server.
2. From the Spotlight Client, click **Configure \| Diagnostic Server \| Federate Diagnostic Servers**.
3. Click **Add**. Select the host of the Spotlight Diagnostic Server. The Spotlight Diagnostic Server should be installed and operational and accessible to the Spotlight Client.


{% include imageClient.html file="figure_federation_Federation-of-DS.png" %}


## On adding a Spotlight Diagnostic Server to the federation

### Monitored connections
The Spotlight Clients connected to the Spotlight Diagnostic Server that has been added to the federation now connect to the federation of Spotlight Diagnostic Server. Spotlight Clients in the federation monitor connections from all Spotlight Diagnostic Server in the federation. Data to / from monitored connections is communicated directly from Spotlight Diagnostic Server to Spotlight Client. It is required that all Spotlight Clients have open communications with all Spotlight Diagnostic Server in the federation.

### Custom views
Spotlight Clients in the federation have access to all custom views in the federation. The custom views from the newly joined Spotlight Diagnostic Server will be accessible to all Spotlight Clients in the federation. Any two custom views with the same name will be merged into the one view.

### Alarm Actions
Spotlight Clients in the federation have access to all Alarm Action rules in the federation. The condition "The Diagnostic Server is…" is added to every pre-existing Alarm Action rule from the newly added Spotlight Diagnostic Server. Do nothing for Alarm Action rules specific to that Spotlight Diagnostic Server. For Alarm Action rules applicable to the federation, remove the condition "The Diagnostic Server is…" and delete duplicate rules.

### Planned Outages
Spotlight Clients in the federation have access to all scheduled planned outages for all Spotlight connections monitored in the federation.

### Configuration templates
Spotlight Clients in the federation have access to all configuration templates in the federation. The configuration templates from the newly joined Spotlight Diagnostic Server will be accessible to all Spotlight Clients in the federation. Any two templates with the same name will both be renamed to remain separate.

### Spotlight license
The Spotlight license applied to the Configuration server is applied to the federation. For more information, see the Configuration server on the  [Configure Operations][enterprise_backend_federation_cfgops] page.

## Reorganizing SSR historical data after creating a federation

If you have created a Federation that monitors connections that were previously monitored by one Diagnostic Server and that Diagnostic Server was storing data to the Spotlight Statistics Repository (SSR) and you want to preserve the historical data in the SSR take the following steps. This should only be done after the Federation has been writing to the SSR for one day to ensure that all connections have been re-created in the new SSR.

### Check the Diagnostic Server list and the data statistics information for each connection

Use the following steps to check how many Diagnostic Servers are in the SSR database and the time period and amount of data collected per connection.
Using SSMS select the SSR database, locate the stored procedure spotlight_merge_data_check_info and execute it to see this information.

### Historical data and the current data are in the same database

Using SSMS expand the SSR database and locate the stored procedure spotlight_merge_data_in_same_ssr. This procedure should be used when you want to move data from an old domain to a currently used domain in the same SSR database. In the SSR the domain is equivalent to the Diagnostic Server host name. This procedure has a parameter called @To_Domain_id which is the id of the domain that you want to transfer the data to. Below is an example of how to use this procedure.

For example say there are three domain ids in your SSR. Domain id 1 is the historical Diagnostic Server which monitored 200 connections before federation. Then these 200 connections were split between two new Diagnostic Servers which have IDs of 2 and 3. Each new DS monitors 100 connections. The new domains will only contain data that was created after federation so you need to merge the data from domain 1 into the new domains 2 and 3 if you want to see the old data.

1. Execute the spotlight_merge_data_in_same_ssr procedure with the parameter @To_domain_id set to 2 which will merge the historical data from domain 1 to the new domain 2.
   exec spotlight_merge_data_in_same_ssr 2  

2. Execute the spotlight_merge_data_in_same_ssr procedure with the parameter @To_domain_id set to 3 which will merge the historical data from domain 1 to the new domain 3.
   exec spotlight_merge_data_in_same_ssr 3  
	
After these two steps the historical data from domain 1 will have been merged to the currently used domains 2 and 3.


### Historical data and the current data are in different database

Using SSMS expand the SSR database and locate the stored spotlight_merge_data_in_diff_ssr. This procedure should be used when you want to move data from an old domain to a currently used domain in a different SSR database. In the SSR the domain is equivalent to the Diagnostic Server host name. This procedure has a parameter called @HistoricalSSRDatabaseName which is the name of the old SSR database that you want to transfer the data from. Below is an example of how to use this procedure.

For example say that you have two SSR databases - SSR_Old and SSR_New. Some of connections appear in both SSR_Old and SSR_New with the same connection name and some of the connections only exist in SSR_Old. Now you want to transfer the data from the SSR_Old to SSR_New.

If the SSR_Old and SSR_New databases are in the same instance then execute spotlight_merge_data_in_diff_ssr with the @HistoricalSSRDatabaseName parameter set to [SSR_Old].
exec spotlight_merge_data_in_diff_ssr "[SSR_Old]"   --execute this line in SSR_New

If the SSR_Old database is in another instance with an IP address of 10.154.10.10 then execute spotlight_merge_data_in_diff_ssr with the @HistoricalSSRDatabaseName parameter set to [10.154.10.10].[SSR_Old].
exec spotlight_merge_data_in_diff_ssr "[10.154.10.10].[SSR_Old]"  --execute this line in SSR_New

Note: Both SSR databases involved in the merge must has the same collation settings.

{% include links.html %}
