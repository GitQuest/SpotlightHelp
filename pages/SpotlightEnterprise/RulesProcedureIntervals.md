---
title: Alarm Evaluation Intervals
sidebar: p_enterprise_sidebar
permalink: RulesProcedureIntervals.html
folder: SpotlightEnterprise
---

<table class="table">
<thead>
	<tr class="head">
		<th>Connection type</th>
		<th>Alarm</th>
		<th>Collection</th>
		<th>Interval</th>
	</tr>
</thead>
<tbody>
	<tr >
		<td>Analysis Services</td>
		<td>Cubes - Days Since Last Processed</td>
		<td>SSAS - Cube List</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Analysis Services</td>
		<td>Command - Long Running Command</td>
		<td>SSAS - Command List</td>
		<td>10 mins</td>
	</tr>
	<tr >
		<td>Diagnostic Server</td>
		<td>In Deadlock</td>
		<td>Deadlock Status</td>
		<td>2 mins</td>
	</tr>
	<tr >
		<td>Diagnostic Server</td>
		<td>In Thread Block</td>
		<td>Deadlock Status</td>
		<td>2 mins</td>
	</tr>
	<tr >
		<td>Diagnostic Server</td>
		<td>Out Of Memory</td>
		<td>Memory Usage</td>
		<td>10 mins</td>
	</tr>
	<tr >
		<td>High Availability</td>
		<td>Availability Group - Failover Availability</td>
		<td>Group States</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>High Availability</td>
		<td>Availability Group - Quorum Failure Imminent</td>
		<td>Group States</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>High Availability</td>
		<td>Availability Group - Synchronization Health</td>
		<td>Availability Group States</td>
		<td>5 mins</td>
	</tr>	
	<tr >
		<td>SQL Server Replication</td>
		<td>Replication - Distribution Latency</td>
		<td>Replication Agents</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server Replication</td>
		<td>Replication - Estimated Time To Apply</td>
		<td>Replication Subscriptions</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server Replication</td>
		<td>Replication - Log Reader Latency</td>
		<td>Replication Agents</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server Replication</td>
		<td>Replication - Publication Expiration</td>
		<td>Replication Publications</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server Replication</td>
		<td>Replication - Subscription Expiration</td>
		<td>Replication Subscriptions</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server Replication</td>
		<td>Replication - Undistributed Commands</td>
		<td>Replication Subscriptions</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL Agent - Alerts</td>
		<td>Alert Failures</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL Agent - Status</td>
		<td>General Counters</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Locks - Blocked Processes</td>
		<td>Blocking List</td>
		<td>2 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>CPU Alarm (for Spotlight Developer only)</td>
		<td>SQL Server CPU Usage (for Spotlight Developer only)</td>
		<td>1 min</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Backup - Days Since Last Full Backup</td>
		<td>Database List</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Backup - Hours Since Last Differential Backup</td>
		<td>Database List</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Backup - Minutes Since Last Log Backup</td>
		<td>Database List</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - Data File Group about to grow</td>
		<td>File Groups</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Locks - Deadlocks</td>
		<td>Deadlock List</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Error Count</td>
		<td>Error Log Scan - Summary</td>
		<td>1 day</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Index Fragmentation</td>
		<td>Fragmentation by Index</td>
		<td>5 AM</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>I/O Stall Time</td>
		<td>Virtual File Statistics</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Latch - Total Wait Time Rate</td>
		<td>Latches Locks</td>
		<td>1 hours</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - Log Flush Wait Time</td>
		<td>Database Info</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Log Shipping - Secondary Latency</td>
		<td>Log Shipping Secondaries</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL Agent - Long Running Jobs (Time) </td>
		<td>Agent Job List</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL Agent - Long Running Jobs (Percent) </td>
		<td>Agent Job List</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL - Long Running SQL</td>
		<td>Long Running SQL</td>
		<td>1 min</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Mirroring - Unrestored Log</td>
		<td>Mirroring</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Mirroring - Unsent Log</td>
		<td>Mirroring</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>User - Response Time</td>
		<td>Response Time</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Memory - Page Life Expectancy</td>
		<td>Buffer Manager</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Poor Performance Health</td>
		<td>Performance Health</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL - Running Out Of Threads</td>
		<td>SQL Server Worker Threads</td>
		<td>1 min</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - Dynamic Data File Group Growths Remaining</td>
		<td>File Groups</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - Dynamic Log File Growths Remaining</td>
		<td>File Groups</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - Data File Group Space Used</td>
		<td>File Groups</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - Log File Space Used</td>
		<td>File Groups</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL Custom Counters</td>
		<td>Custom Counters - SQL Server</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Databases - SQL I/O Errors</td>
		<td>Global Variables</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Network - SQL Server Packets Error Rate</td>
		<td>Global Variables</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Compiles - Percentage Recompilations</td>
		<td>Statistics</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Fatal Current Process Error (severity level 20)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Fatal Database Integrity Suspect Error (severity level 23)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Fatal Database (dbid) Processes Error (severity level 21)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Fatal Hardware Error (severity level 24)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Fatal Hardware Error (severity level 25)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Fatal Table Integrity Suspect Error (severity level 22)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - High Severity Message</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Information Severity Message</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Low Severity Message</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Medium Severity Message</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Error Log - Critical Error (severity level lower than 20)</td>
		<td>Error Log Scan - Detailed</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Tempdb Contention</td>
		<td>Tempdb Contention</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Tempdb Version Store Generation Rate</td>
		<td>Tempdb Performance Counters</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>Tempdb Version Store Size</td>
		<td>Tempdb Space Usage</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>User - Connection Count</td>
		<td>SQL Server Connections</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>User - Logins Per Second</td>
		<td>Global Variables</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>SQL Server</td>
		<td>SQL Virtual Log Files Count</td>
		<td>SQL Virtual Log Files Count</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Blocked Processes</td>
		<td>Processors</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>CPU Usage</td>
		<td>Processors</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>File System Space</td>
		<td>Filesystem_Space</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Hyper-V CPU Wait Time per Dispatch</td>
		<td>Hyper-V - Virtual Machine Data</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Hyper-V Virtual Machine Heartbeat</td>
		<td>Hyper-V - Virtual Machine Data</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Hyper-V - Virtual Overhead</td>
		<td>Hyper-V - Virtual Machine Data</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Most Active Disk</td>
		<td>Disk_Activity</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Network Errors In</td>
		<td>Network</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Network Errors Out</td>
		<td>Network</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Paging In</td>
		<td>Paging</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Paging Out</td>
		<td>Paging</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Memory - Physical Memory Available</td>
		<td>TotalRAM</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Swapping In</td>
		<td>Processors</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>SwappingOut</td>
		<td>Processors</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Swap Space</td>
		<td>Swap</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>VMware - Virtual Machine Heartbeat </td>
		<td>Virtual Machine Usage</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>VMware - Virtual Overhead</td>
		<td>Virtual Machine Usage</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>VMware - Memory Repossessed</td>
		<td>Virtual Machine Usage</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>UNIX/Linux</td>
		<td>Zombie Processes</td>
		<td>Process_Counts</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Network - Percentage Bandwidth</td>
		<td>Network</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>CPU - Average CPU Usage</td>
		<td>Processors</td>
		<td>1 min</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Windows Custom Counters</td>
		<td>Custom Counters - Windows</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Disks - Free Space</td>
		<td>File Systems</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Disks - Percentage Used</td>
		<td>File Systems</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Disks - Queue Length</td>
		<td>Logical Disks</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Disks - Transfer Time</td>
		<td>Physical Disks</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>File - Exceeded Set Size</td>
		<td>File Sizes</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Memory - Free System Page Table Entries</td>
		<td>Memory</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Hyper-V CPU Wait Time per Dispatch</td>
		<td>Hyper-V - Virtual Machine Data</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Hyper-V Virtual Machine Heartbeat</td>
		<td>Hyper-V - Virtual Machine Data</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Hyper-V - Virtual Overhead</td>
		<td>Hyper-V - Virtual Machine Data</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>CPU - Individual CPU Usage</td>
		<td>Processors</td>
		<td>1 min</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Paging - Disk Activity</td>
		<td>Paging Disk Activity</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Memory - Physical Memory Available</td>
		<td>Memory</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>CPU - Processor Queue Length</td>
		<td>System Performance</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>Memory - Percentage Free Virtual Memory</td>
		<td>Memory</td>
		<td>6 hour</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>VMware - Virtual Machine Heartbeat </td>
		<td>Virtual Machine Usage</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>VMware - Virtual Overhead</td>
		<td>Virtual Machine Usage</td>
		<td>5 mins</td>
	</tr>
	<tr >
		<td>Windows</td>
		<td>VMware - Memory Repossessed</td>
		<td>Virtual Machine Usage</td>
		<td>5 mins</td>
	</tr>
</tbody>
</table>
	  