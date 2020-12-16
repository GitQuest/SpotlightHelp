---
title: Databases drilldown
last_updated: October 16, 2017
summary: "Drilldown on the details of all databases in SQL Server."
sidebar: c_sqlserver_sidebar
permalink: sqlserver_drilldown_databases.html
folder: ConnectSQLServer
---


## How to open the Databases drilldown

From the Spotlight Client

1. Select the connection from the left Connections pane.
2. Click **Monitor \| Databases** from the ribbon.
   {% include imageClient.html file="tb_drilldown_databases.png" alt="Databases drilldown for SQL Server" %}

{% include tip.html content="Click for more information on using [Spotlight Charts][enterprise_display_charts] and [Spotlight Grids][enterprise_display_grids]." %}


## About the Databases drilldown


### Databases grid

Shows details of all databases in SQL Server. Select one or more databases in the Databases grid to show just those databases in **Database Details**. Press the **Shift** key to select a block of multiple databases or the **CTRL** key to select individual databases.

{% include inline_imageClient.html file="tb_drilldown_database_view.png" alt="Database view" %} | Click to select the Database View as: **Overview, Transactions, Backup Status, Properties or In-Memory** to adjust the category of information displayed in the Databases grid.
{% include inline_imageClient.html file="tb_drilldown_databases_showhide.png" alt="show/hide" %} | Click to hide/show the Databases grid.

{% include tip.html content="The **tempdb** database has its own drilldown. Click on tempdb to open the tempdb drilldown. Click on another cell in the tempdb row to select tempdb for **Database Details**." %}

{% include tip.html content="The # Tables column may not match the number of tables shown in the **Tables grid**. This is most evident when viewing table details for the tempdb database and is due to its dynamic nature." %}


### Summary page
Investigate disk space usage and recent I/O activity.

#### Database Space chart
Shows the disk space usage for databases, displayed in megabytes or as a percentage. To switch between statistics, click the arrow next to the chart name.

Data components are broken down into space used by:

* Data Used
* Data Free (not allocated to any tables/indexes)

Logs are broken down into:

* Log Used space
* Log Free space

#### Database History chart
Shows various statistics relating to recent I/O activity on each database.

The following statistics are displayed:

**% Log Used** - The amount of file space allocated to the transaction log of each database that is currently used. Log space can be freed up by backing up the log, or truncating it (backup log <dbname> with truncate_only). All log records that exist after the oldest open transaction cannot be freed.

**Data File Size MB** - The amount of disk space that the data files are using. This graph shows how the size of data files have changed over time.

**Log File Size MB** - The amount of disk space that the log files are using. This graph shows how the size of log files have changed over time.

**Active Transactions** - The number of open transactions in each database.

**Transactions Rate** - The rate of transactions for each database.

**Log Cache Hit Rate** - How much read I/O is being saved by caching log data. The log caches will normally only have a non-zero hit rate if there is Rollback activity occurring.

**BCP Throughput Rate** - The rate (measured in kilobytes per second) at which data is being loaded into the database using BCP (Bulk Copy Program) or BULK INSERT. While BCP and BULK INSERT are the fastest ways of getting data into SQL Server, you can expect performance to be degraded for other users while they run.

**Backup Throughput Rate** - The rate at which backup or restore commands are reading or writing to the database. While backups are essential, you can expect performance to be degraded for other users while they run.

**DBCC Scan Bytes Rate** -  The rate at which Database Consistency Checks (DBCCs) are processing data. While regularly running DBCC is advisable to ensure the consistency of your databases, you can expect performance to be degraded for other users while they run.

**Log Flushes Rate** - The rate at which the log cache for each database is being flushed to disk, which is necessary to guarantee that transactions can be recovered in the event of a system failure. The most common cause of a log flush is a user issuing a commit transaction.

**Log Flush Wait Time (ms)** - The amount of time spent waiting for log flushes in each database. High log flush wait time can be caused by a slow or overworked disk subsystem. If a database has a consistently high Log Flush Wait Time that never changes, run SQL command CHECKPOINT on that database to force another log flush, and check the value in Spotlight Enterprise again.

**Log Growths Rate** - The number of times the log has been expanded for each database.

**Log Shrinks Rate** - The number of times the log has been reduced for each database.

**Log Truncations Rate** - The frequency of log truncations for each database. This can be caused by manual truncations (backup log <dbname> with truncate_only), or automatically if the database has the trunc. log on chkpt. option turned on.


* To switch between statistics, click the arrow next to the chart name.
* You can restrict the database(s) that are displayed in the Summary page by selecting the database(s) in the Databases grid that you are interested in.  



### File Groups page

#### File Groups grid
Shows all file groups in the selected databases, including their file count, used space, and free space.

You can restrict the file groups included in the charts by highlighting just the records you are interested in.

#### File Group Space chart
Shows the amount of space allocated to each file group, displayed in megabytes or as a percentage. Each file group consists of space that is used and space that is free (not yet allocated to any tables or indexes).

To switch between statistics, click the arrow next to the chart name.

#### File Group Growth chart
Shows the amount by which each file group is growing over time.


### Data Files page

#### Data Files grid
Shows all files (excluding the Transaction Log) in the selected databases, including their size, free space, and maximum size the file can grow to.

To filter the files displayed in the grid, type a file group name into the File Group field and then click Apply Filter. Only those files that belong to the specified file group are displayed in the grid. You can use the percent sign (%) as a wildcard.

#### Data Files Space chart
Shows the amount of space allocated to the data file for the selected database in megabytes or as a percentage, broken down into used and free space. To switch between statistics click the arrow next to the chart name.

#### Data Files Growth chart
Shows the amount by which each file is growing over time, displayed as file used MB or file total MB. To switch between statistics, click the arrow next to the chart name.


### Transaction Logs page

#### Transaction Logs grid
Shows all transaction logs in the selected databases including their size, free space, and the list of disks on which their file group resides.

You can restrict the transaction logs included in the charts by highlighting just the records you are interested in.

#### Transaction Log Space chart
Shows used space and free space for the transaction logs, displayed in megabytes or as a percentage. To switch between statistics, click the arrow next to the chart name.

#### Transaction Log Growth chart
Shows the amount by which each transaction log is growing over time.


### Log Files page

#### Log Files grid
Shows all log files in the selected databases, including their size, free space and maximum size the file can grow to.

You can restrict the log files included in the charts by highlighting just the records you are interested in.

#### Log File Space charts
Shows the total space allocated to each log file, displayed in megabytes or as a percentage of disk space. To switch between the charts, click the arrow next to the chart name.

#### Growth charts
Shows the amount by which each log file is growing over time. To switch between the charts, click the arrow next to the chart name.


### Tables page
Investigate Tables, table space, and table growth.

#### Tables grid
Shows all tables in the selected databases, including their size, number of rows, free space and the partition on which they reside.

The number of tables shown in the Tables grid may not match the number displayed in the # Tables column of the Databases grid. This is most evident when viewing table details for the tempdb database and is due to its dynamic nature.

You can filter the results displayed in the Tables grid by the following criteria:

* Top N tables by size or row count
* Data Space name
* Table name

To filter the results, type appropriate values into the fields above the Tables grid (wildcards are supported) and then click **Apply Filter**.

#### Table Space chart
Shows the amount of space used by each table, displayed in megabytes or as the number of rows. To switch between megabytes and rows, click the arrow next to the chart name.

#### Table Growth chart
Shows the amounts by which each table is growing over time, displayed in megabytes or as the number of rows. To switch between megabytes and rows, click the arrow next to the chart name.


### Indexes page
Investigate Index distribution statistics.

#### Indexes grid
Shows the index statistics for all indexes in the selected tables. SQL Server stores statistics about the distribution of the key values in each index, and uses these statistics to determine which index(es) to use in query processing. SQL Server can be configured to automatically maintain the index statistics for you, or they can be maintained manually using Transact-SQL commands.

When you first display the Indexes page, by default the top 50 indexes by size are displayed in the grid.

You can filter the results displayed in the Indexes grid by the following criteria:

* Top N Indexes by size, row count, heaps only, clustered only, or non-clustered only
* Data Space name
* Index name

To filter the result in the Spotlight Client, type appropriate values into the fields above the Indexes grid (wildcards are supported) and then click **Apply Filter**.

The **Update Statistics** option can be used to (re)collect index distribution statistics for the selected index(es). This option runs an UPDATE STATISTICS command on each of the selected indexes. This collects the latest index statistics for each index. To update statistics, in the Spotlight Client right-click an entry in the Indexes table and select **Update Statistics**.

You should update index statistics whenever:

* There have been significant changes in the key values in the index. This can be seen in the RowModCtr column.
* A large amount of data in an indexed column has been added, changed, or removed (that is, if the distribution of key values has changed), or the table has been truncated using the TRUNCATE TABLE statement and then re-populated.

* Selecting a single row in this grid shows detailed index statistics for that index in the lower section of the drilldown.
* In the Spotlight Client only members of the Spotlight Diagnostic Administrators group can use the Update Statistics option.


#### Index Statistics Summary
Shows further statistics for the selected indexes.

**Density** - Density is the term used by SQL Server to represent the selectivity of the index columns. The more selective an index is, the more useful it is in searches. Density values range from 0% to 100%. A unique index will have a Density value of 1/<#rows in table>. Generally, density values of 10% or lower are highly selective indexes. Density can be difficult to interpret as the value is a function of the number of records in the table.

**Avg Key length** - The average length of all the index columns.

**Last Updated** - The time and date that the statistics were last updated.

**Rows** - The number of rows in the index.

#### Indexes Density grid
When a single index is selected in the Indexes grid, the Density grid shows the density values for each combination of columns in the index.

The Density values shown in this grid derive from the latest statistics for the selected index. If the index statistics are out of date, so too will these values be. Check the Last Updated statistic on the Statistics sub-page for the date on which statistics where last collected. Use the Update Statistics option (available by right-clicking an entry in the Indexes table) to re-collect statistics. Only members of the Spotlight Diagnostic Administrators group can use the Update Statistics option.

#### Index Distribution chart
When a single index is selected in the Indexes grid above, the Index Distribution chart shows the index distribution histogram for that index.

When SQL Server collects statistics on an index to determine its usefulness for resolving queries, it samples the data in the index and produces a histogram of the key values found. The Index Distribution chart shows that histogram for the selected index.

The values shown here are from the latest statistics for the selected index. If the index statistics are out of date, then so too will these values be. Check the Last Updated statistic on the Statistics page for the date when statistics were last collected. Use the Update Statistics option (available by right-clicking an entry in the Indexes table) to re-collect statistics. Only members of the Spotlight Diagnostic Administrators group can use the Update Statistics option.

Each series in the chart corresponds to one sample value from the first column in the index. The chart shows the number of rows in the table that have that value.

Note that SQL Server uses sampling only and does not inspect every key value. The histogram shows the percentage of the table that have that value. Not all of the records counted will have the exact sample value shown.

**Example**
If the selected index was on a Name column, the graph might show values:

```
ABRAHAM: 5

GEORGE: 20

PETER: 25

STEVEN: 30

ZACH: 20
```

This means 5 of the people have a name alphabetically less than or equal to ABRAHAM, 20 are between ABRAHAM and GEORGE, 25 between GEORGE & PETER etc.

This chart can be used to identify skewed indexes. These are indexes that have a very uneven distribution of data. For example, if 95% of the table has the same value for a key, it is difficult for SQL Server to determine if it is a useful index or not. Searches on values that fall in the 5% range may find the index very useful, but searching on values that occur 95% of the time is not so useful.

#### Fragmentation grid
Shows fragmentation information for all indexes in the SQL Server database. Note that collecting and examining fragmentation information can take considerable time and put significant load on your server.

For information about the Fragmentation statistics displayed on the Fragmentation page see the sys.dm_db_index_physical_stats DMV.

##### Types of Fragmentation
The following types of fragmentation can occur in SQL Server tables: Internal and External.

* Internal Fragmentation is the term used when your index pages have a considerable amount of free space in them. In this case, each index page is only partially used, and the index takes up more disk space than it really needs. Extra I/O operations will be required to read the same number of index entries. Note that creating indexes with high Fill Factor values will cause internal fragmentation.
* External Fragmentation is the term given to the case where the logical order of the pages does not match the physical order on disk, or when the extents belonging to the table are not contiguous. This case only affects performance when SQL Server does ordered scans of all, or part of, the table or index. Examples of operations that could require ordered scans are Range queries (WHERE Column between X and Y, Where Column > z etc) and some join, sort, and grouping operations.

External Fragmentation can be categorized into the following types: Logical and Extent.

* Logical Scan Fragmentation is where the logical order of the pages does not match the physical order on disk.
* Extent Scan Fragmentation is where extents, on which the index resides, are not contiguous.

Both Internal and External fragmentation can occur when data is modified in the table (e.g. INSERT, UPDATE, and DELETE statements). Because of these data modifications, pages can be split or merged together, and the fullness of each page can vary over time. For queries that scan part or all of a table, fragmentation can cause additional page reads, which can degrade performance.

Fragmentation can impact performance in the following ways:

* Less data fits on each page. High internal fragmentation causes less data to be stored on each page. This can impact performance in the following ways. Firstly, for operations that must access many pages (such as table and index scans), the fact that there is wasted space on each page means that more pages have to be read to access the same amount of data. Secondly, when pages are loaded into SQL Server's memory cache, more memory is required to hold the same amount of data (or conversely, less data can be held in the same amount of memory). This can cause lower Buffer Cache hit ratios and higher I/O rates. This second point can impact the performance of any SQL query, as it lowers the chance of finding required pages already in memory.
* Table and Index scans. High external fragmentation can impact SQL Server performance only for full or partial table and index scans. When SQL Server has to read table or index pages in logical order, external fragmentation can cause SQL Server to perform extra I/O and processing. In general, if you do not perform many table or index scans, then external fragmentation will not cause performance problems. Most online, OLTP, or web applications use direct index lookups to access the required data in a few read operations. These types of applications will typically not suffer any performance degradation when the database has high external fragmentation.

##### How fragmented are my tables?
Five values can be used to determine the overall fragmentation in your tables:

* Extent Scan Fragmentation and Logical Scan Fragmentation are the most important ones. These are expressed as percentage values, and the lower the value, the less fragmentation there is. Note that both these Scan Fragmentation values are meaningless for Heaps (tables without indexes). Also, Logical Scan Fragmentation is meaningless for text structures. Spotlight Enterprise displays a value of -1 for these index types when either of these are the case.
* Average Page Density shows you how full each page is. This will be affected by the FILL FACTOR setting used when creating the index. For example, immediately after creating an index with a FILL FACTOR of 30, the Average Page Density for that index will be 30. This value will then change as data in the table is modified. Average Page Density can be thought of as the "real" fill factor at the time the data was collected, as opposed to the "original" fill factor that was specified when the index was created. The Original Fill Factor is used when an index is created to leave free space in index pages, and allow for the insertion of new records without having to split the page. Because Average Page Density is based on the original fill factor, there are no hard and fast rules to determine what is good and bad.  In general, a higher value indicates low internal fragmentation.
* Fill Factor Variance is a statistic computed by Spotlight Enterprise to compare the Average Page Density with the original fill factor that was used when the index was created. It is calculated as the absolute difference between Average Page Density and Original Fill Factor. It shows you how much the fill factor of the index has changed since it was created. A high value indicates high internal fragmentation.
* Scan Density is a value computed by dividing the optimal number of extent switches by the actual number of extent switches. It gives you an indication of how much external fragmentation exists. It is expressed as a percentage value, where higher values indicate less fragmentation.  Scan density is meaningless when your table resides on more than one file. Spotlight Enterprise displays a value of -1 when this is the case.

##### Removing Fragmentation
There are several options available to eliminate (or at least reduce) fragmentation. In general, you need to get SQL Server to rebuild the indexes that are fragmented.

The following are the best methods for reducing fragmentation:

* DBCC DBREINDEX can be used to rebuild all indexes on the table. Users cannot access the table while this command runs.
* Running DROP INDEX and CREATE INDEX to rebuild the indexes will eliminate any fragmentation. However, this can be complicated when the index you need to defrag supports a constraint such as a Primary Key. SQL Server will not let you drop the primary key while there are foreign keys referencing it. This problem can be alleviated somewhat by using the DROP_EXISTING clause of CREATE INDEX. Again, the table will be unavailable to users while this runs.

### Disk Space page
How much space database files are using on each disk

{% include note.html content="The Disk Space page is not supported for SQL Server hosted on Unix/Linux operating systems." %}

#### Disk Space chart
Shows each logical disk on the server, and allocates the space on each disk into either SQL Data files, SQL Log files, Non-SQL files or Free Space. You can easily see how much of each disk is used by SQL databases, and how much is free.


##### Tips to using the Disk Space chart in the Spotlight Client

* To switch between Disk Space Utilization by megabytes and Disk Space Utilization by percent, click the arrow next to the chart name.
* Select one or more of the databases in the Databases grid to restrict the Data and Log figures to only the space used by those databases.
* The space shown for SQL Data and Log files refers to files in this instance of SQL Server only.  If there are multiple SQL Server instances on this server, the data/log files for other instances will be included in the Non-SQL Files figure.
* If the Windows server being monitored does not have Logical Disk performance counters enabled, the Non-SQL Files component of this chart will always be zero. If disk counters are not enabled, the Disk Counters Disabled alarm will be shown on the Spotlight Overview page. To enable disk counters, run the Windows command diskperf -y and restart the server.  


### LiteSpeed backups page
Show the history of my LiteSpeed backups

#### LiteSpeed Backup History grid
For databases backed up using LiteSpeed for SQL Server, use to view the history of your backups.

Requirements

* Designed for use with LiteSpeed for SQL Server versions 7.1 and above.
* Requires that LiteSpeed be installed and operational on your SQL Server network.


### Fragmented Indexes page
Use the Fragmented Indexes grid to assess the fragmentation of index partitions on the SQL Server.

#### Data collection
The data for this grid is collected once a day and stored in the Playback Database.

{% include note.html content="To re-collect the data now, select the criteria and click **Collect now**. This could put significant load on the SQL Server. It is advisable to collect fragmentation information during a quiet period." %}

#### Collection criteria definitions
The criteria by which data is collected (Defaults are set by [Configure Defragmentation Check][enterprise_cfgmonitor_defragcheck]):

* Top (most) fragmented indexes
* Database name
* Minimum Size - 10MB = 1280 pages
* Minimum operations - minimum number of either scan or update operations.

#### How to customize the criteria for the default collection
To customize the collection schedule for the default collection, use the Spotlight Client. Click **Configure \| Scheduling** select the connection and customize the **Fragmentation by Index** schedule.

To customize the criteria used to collect the data, use the Spotlight Client. Click **Configure \| Defragmentation Collection**. See [Configure Defragmentation Check][enterprise_cfgmonitor_defragcheck].
   {% include imageClient.html file="tb_config_defrag.png" alt="Configure Defragmentation Collection" %}


#### How to defragment an index

1. Select an index to defragment and click **Generate Defragmentation Script**.
2. Use SQL Server Management Studio to schedule a job to run this script during a quiet period.

{% include note.html content="Execution of this script could put significant load on the SQL Server." %}

#### Playback

{% include note.html content="When in Playback, history will not be displayed for the Fragmented Indexes grid." %}


{% include links.html %}
