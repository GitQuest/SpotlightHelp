---
title: How to configure WMI with minimum required user permissions
last_updated: July 29, 2016
summary: "In some environments it may not be feasible for Spotlight to connect to the Windows server with an account that is a member of the Administrators group. The following instructions are provided for these environments. Note that there are known issues with this procedure as documented below."
sidebar: c_windows_sidebar
permalink: windows_connect_wmiminimumpermissions.html
folder: ConnectWindows
---
 


## Known Issues

### The OpenSessions collection

The OpenSessions collection sends a list of the open Windows network sessions to your server. The list includes who is connected and from where, how long they have been connected and how many files they have open.

The OpenSessions collection is used in:

* The Windows Server \| Spotlight Overview page \| Network Panel \| Open Sessions count.
* The Windows Server \| Network Drilldown \| Sessions page.

Spotlight does not alarm on this data.

### The Physical Disk Drive collection

The Physical Disk Drive collection populates the Windows Server \| Disks Drilldown \| Disk Summary page. This drilldown contains a list of the physical disks installed on the server. Its data is relatively static as it only changes when disks are added, removed or re-partitioned.

Inside of this known issue a Generic Failure error will be returned.


## 1. Setup permission to read data

{% include note.html content="For the following instructions, *Spotlight User* is the windows user that will be used to authenticate the Spotlight connection to the Windows server as per: [Windows Server \| Connection Details][windows_connect_details]" %}

1. Click **Control Panel \| Administrative Tools \| Computer Management** to open the Computer Management dialog.
2. Double click **Local Users and Groups \| Groups**.
3. Double click **Performance Log Users**. Add the *Spotlight User* to this group. **OK**.
4. Double click **Performance Monitor Users**. Add the *Spotlight User* to this group. **OK**.


## 2. Grant permissions to get information about services

### Retrieve the user SID

From the Windows command prompt, type **powershell** and click **Enter** to open the Powershell.

Run the following command to retrieve the user SID of the *Spotlight User*. Replace **domainName** and **userName** with the domain name and user name for the *Spotlight User* account.

```
[wmi]"win32_useraccount.domain='domainName',name='userName'"
```

### Retrieve the current SDDL for the Services Control Manager

From the Windows command prompt, run the following command to retrieve the current SDDL for the Services Control Manager. The SDDL is saved in the file called file.txt.

```
sc sdshow scmanager > file.txt
```

The SDDL looks something like this. For more information see Microsoft KB914392.

```
D:(A;;CC;;;AU)(A;;CCLCRPRC;;;IU)(A;;CCLCRPRC;;;SU)(A;;CCLCRPWPRC;;;SY)(A;;KA;;;BA)S:(AU;FA;KA;;;WD)(AU;OIIOFA;GA;;;WD)
```

### Modify the SDDL

Copy the section of the SDDL that ends in IU (Interactive Users). This section is one complete bracketed clause ie (A;;CCLCRPRC;;;IU). Paste this clause directly after the clause you copied from.

In the new text, replace IU with the user SID of the *Spotlight User*.

The new SDDL looks something like the following:

```
D:(A;;CC;;;AU)(A;;CCLCRPRC;;;IU) (A;;CCLCRPRC;;;S-1-5-21-214A909598-1293495619-13Z157935-75714)(A;;CCLCRPRC;;;SU)(A;;CCLCRPWPRC;;;SY)(A;;KA;;;BA) S:(AU;FA;KA;;;WD)(AU;OIIOFA;GA;;;WD)
```

### Set the security credentials for accessing the Service Control Manager

The sdset command on sc sets the security credentials for accessing the Service Control Manager (scmanager). Note the permissions on scmanager are being replaced. Setting security credentials is not additive. That’s why we needed to copy the existing permissions.

```
sc sdset scmanager "D:(A;;CC;;;AU)(A;;CCLCRPRC;;;IU)(A;;CCLCRPRC;;;SU)(A;;CCLCRPWPRC;;;SY)(A;;KA;;;BA)(A;;CCLCRPRC;;;S-1-5-21-214A909598-1293495619-13Z157935-75714)S:(AU;FA;KA;;;WD)(AU;OIIOFA;GA;;;WD)"
```

## 3. Provide access to the Registry keys used by Spotlight


On the Windows server and/or Windows host of the database connection in RegEdit open the following nodes.

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control

On each node

1. Right click and select **Permissions**.
2. Add the *Spotlight User*. **OK**.
3. Select the *Spotlight User*. Select **Read access**.


## 4. Run Windows Component Services

From the Windows command prompt, type **dcomcnfg** and click **Enter** to open the Component Services dialog.

### Configure COM security

1. From the Component Services dialog click **Computers \| My Computer**.
2. Right click **My Computer** and select **Properties**.
3. From the Properties dialog, click **COM Security**.
4. From Access Permissions, click **Edit Limits**.
    1. Add the *Spotlight User*.
    2. Allow **Remote Access**.
    3. Click **OK** to close the Access Permission dialog and save changes.
5. From Launch and Activation Permissions, click **Edit Limits**.
    1. Add the *Spotlight User*.
    2. Allow **Remote Launch** and **Remote Activation**.
    3. Click **OK** to close the Launch and Activation Permission dialog.
6. Click **Ok** to close the Properties dialog and save changes.

### Configure DCOM security

1. From the Component Services dialog double click **Computers \| My Computer \| DCOM Config \| Windows Management and Instrumentation**.
2. Right click **Windows Management and Instrumentation \| Properties**.
3. Click **Security \|  Launch and Activation Permissions \| Edit**.
    1. Add the *Spotlight User*.
    2. Allow **Remote Launch and Remote Activation**.
    3. Click **OK** to close the Launch and Activation Permission dialog and save changes.
4. Click **OK** to close the Windows Management and Instrumentation Properties dialog and save changes.


## 5. Configure WMI permissions

From the Windows command prompt, type **wmimgmt.msc** and click **Enter** to open the WmiMgmt dialog.

1. Right click **WMI Control (Local) \| Properties**.
2. Click **Security**.
3. Expand the **Root node**. Select **cimv2**.
4. Click the **Security** button to open security settings for WMI on this computer.
5. Click **Advanced** to open the advanced security settings for this WMI namespace.

    Add the *Spotlight User*. Click **Edit**. Allow:

    * Execute Methods
    * Enable Account
    * Remote Enable
    * Read Security

    Ensure these permissions apply to this namespace and all the namespaces under it by selecting **This namespace and subnamespaces** in the Apply to drop down box.

    Click **OK** to save the new permissions.

6. Click **OK** to close the Advanced Security Settings dialog. Click **OK** to close the Security for ROOT dialog.
7. Returning to the Root node, select **DEFAULT**.
8. Click the **Security** button to open security settings for DEFAULT.
9. Click **Advanced** to open the advanced security settings.

    Add the *Spotlight User*. Click **Edit**. Allow:

    * Execute Methods
    * Enable Account
    * Remote Enable
    * Read Security

    Ensure these permissions apply to this namespace and all the namespaces under it by selecting **This namespace and subnamespaces** in the Apply to drop down box.

    Click **OK** to save the new permissions.

10. Click **OK** to close all dialogs.
11. Add this user to the monitored Windows server Power User group and then restart the server's Windows Management Instrumentation service. This step is optional but it will fix the Open Sessions and Session page no data issue.


{% include links.html %}
