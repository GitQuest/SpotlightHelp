---
title: The Spotlight Report Viewer
keywords: reports
summary: "Spotlight reports are displayed in the Spotight Report Viewer."
sidebar: p_enterprise_sidebar
permalink: enterprise_display_reportviewer.html
id: 320
folder: SpotlightEnterprise
---

## Using the Report Viewer
From the Spotlight Client

1. Click **Reports** to show the reports that are available from this Spotlight Client.
2. Select a report from the [List of Reports][enterprise_display_reportsshipped].
3. If SQL Server authentication is required, enter the user and password details.
4. Fill in the input parameters. These vary but many require the start date, end date and connection name.
5. Click **View Report**.

### Save / Export
Save reports in PDF, or as an .xls (Microsoft Excel) file using the **Save** icon on the Report toolbar.

### Print, search, refresh
Print, search, and refresh reports using the Report toolbar.

### Generate a different report / change the input parameters
To generate a different report, select the report from the Report list at the top of the Spotlight Report Viewer. Update the input fields if required then click **View Report**.

If you change the report criteria (time frame or Connection Name) you must click **View Report** in order to see an updated version of the report.



## Can I customize the reports to my own criteria?
The Spotlight Report Viewer displays reports using SQL Server 2005 or 2008 Report Definition Language files (.rdl). The supplied reports will be shown below the node "Default Reports" and the customized reports will be shown below the "Custom Reports".

### Customize supplied reports
Copy the definition (rdl) files in the Spotlight Client installation folder in the Plug-ins\Trending\Reports to \<user\>\Documents\Spotlight Reports and rename the copied rerpots, then you can use Microsoft Visual Studio 2008 to customize the Reports.
### Create new reports
use Microsoft Visual Studio 2008 to create your onw reports, you can refer to  [Query the Spotlight Statistics Repository][enterprise_ssrquery],to retrie data from Spotlight Statistics Repository database tables directly or via supplied stored procedures.

## Where is the data? Can I customize the collection schedules? (Move the section to Spotlight Reports)
Data is collected from the SQL Server instance then written to the Spotlight Statistics Repository.

You can customize the collection schedules in the Spotlight Client. See [Configure Scheduling][enterprise_cfgmonitor_scheduling].


{% include links.html %}
