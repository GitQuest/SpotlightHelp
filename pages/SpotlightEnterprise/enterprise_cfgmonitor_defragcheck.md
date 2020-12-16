---
title: Configure Defragmentation Check
last_updated: September 13, 2017
tags: [configure_monitoring,apply_configuration_to]
summary: "Configure the criteria used to collect data for the SQL Server | Databases drilldown | Fragmented indexes page"
sidebar: p_enterprise_sidebar
permalink: enterprise_cfgmonitor_defragcheck.html
id: 190
folder: SpotlightEnterprise
---


The SQL Server \| Databases drilldown \| Fragmented Indexes page is used to assess the fragmentation of index partitions on the SQL Server. Data for the Fragmented indexes page is collected once a day according to the following criteria and stored in the Playback Database.

## Configure Defragmentation Check from the Spotlight Client

Click {% include inline_imageClient.html file="tb_config_defrag.png" alt="Configure Defragmentation Collection" %} **Configure \| Defragmentation Collection**.

## Select template or connection to configure

Select the SQL Server connection from the list of available options. Spotlight will show the configuration for that connection. Make changes if required. Optionally use the options at the bottom of the screen to apply the same configuration to other SQL Server connections or save the configuration as a template.

Alternatively, select a template to configure. The templates you have previously saved for SQL Server Defragmentation Check are listed. On selecting the template you can view / modify / reapply the template configuration. You can delete or rename the template. For more information, see [Configuration templates][enterprise_cfgmonitor_templates].

## Override or use the factory settings

### Override the factory settings

Select the **Override the factory settings** option to modify the settings for the selected template or connection.

### Use factory settings

Clear the **Override the factory settings** option to return the settings for the selected template or connection to the Factory Settings. These are the settings that were shipped with Spotlight.


## Configuration

### Select Database(s)
Apply this configuration to all databases or a selected database.

* Select **All** to apply this configuration to all databases. (Default)
* Select **Specify Database** and select the database to apply this configuration to.

### Minimum Size
Set the minimum size count. Default 10MB = 1280 pages

### Minimum Usage operations
Set the minimum number of either scan or update operations. Default 5.

### Show Top
Set to collect top (number of) most fragmented indexes. Default 10 partitions by avg. fragmentation %.

## Reuse this configuration

### Apply configuration to…  

Optionally, apply this configuration to other connections.

### Save to Template  

Optionally, save this configuration to a template. Where a template has been selected to configure you will also see options to **Delete** or **Rename** the template. For more information on Templates, see [Configuration templates][enterprise_cfgmonitor_templates].


## Close the dialog

### OK

Save changes to the configuration for the selected connection or template.

### Cancel

Discard changes to this screen.


{% include links.html %}
