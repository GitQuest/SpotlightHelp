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

## SSR historical data process while making a federation

### Check the Diagnostic Server list and the data statistics information for each connection
In SSMS, select the SSR database, there is a stored procedure - spotlight_merge_data_check_info, execute it, will get these information.


### Historical data and the current data are in the same database
In SSMS, expand the SSR database, there is a stored procedure - spotlight_merge_data_in_same_ssr, it has a parameter: @To_Domain_id. This procedure can merge data from an old domain to currently used domain. Below is an example to show how to use this procedure.

For example, there are three domain id in the SSR, the 1 is historical Diagnostic Server which monitored 200 connections before we use federation. Then we split these 200 connections to two new DS, the ID is 2 and 3, each new DS monitors 100 connections. We found the new domain only contains the data after federation, we want to merge the data from domain 1 into the new domain 2 and 3.
 
1. Execute the spotlight_merge_data_in_same_ssr with the @To_domain_id value is 2 to merge the historical data from other domains to the current domain 2.
    exec spotlight_merge_data_in_same_ssr 2  
2. Execute the spotlight_merge_data_in_same_ssr with the @To_domain_id value is 3 to merge the historical data from other domains to the current domain 3.
    exec spotlight_merge_data_in_same_ssr 3
	
After these two steps, the historical data will been merged to the Current used domains 2 and 3.


### Historical data and the current data are in different database

In SSMS, expand the SSR database, there is a stored procedure - spotlight_merge_data_in_diff_ssr, it has a parameter: @HistoricalSSRDatabaseName. This procedure can merge the data from an historical SSR database to the currently used SSR database. Below is an example to show how to use this procedure.

For example, we have two SSR databases - SSR_Old and SSR_New, some of connections appear in both SSR_Old and SSR_New with the same connection name and some of the connections only exist in SSR_Old. Now we want to transfer the data from the SSR_Old to SSR_New:
1. If the connection name in both SSR database, merge to the exist connection in SSR_New;
2. If the connection name not in SSR_New, add the connection and the data into SSR_New;    

If SSR_Old and SSR_New are in the same database instance, execute spotlight_merge_data_in_diff_ssr with the @HistoricalSSRDatabaseName value is [SSR_Old].
exec spotlight_merge_data_in_diff_ssr "[SSR_Old]"

If SSR_Old is in another database instance with an IP 10.154.10.10, spotlight_merge_data_in_diff_ssr with the @HistoricalSSRDatabaseName value is [10.154.10.10].[SSR_Old].
exec spotlight_merge_data_in_diff_ssr "[10.154.10.10].[SSR_Old]"

Note:  SSR databases used to merge should has the same COLLATE settings.

{% include links.html %}
