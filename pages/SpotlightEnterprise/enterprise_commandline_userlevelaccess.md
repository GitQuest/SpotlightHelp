---
title: Windows Powershell / Manage access to Spotlight connections Command line
summary: "Manage access to Spotlight connections from Windows Powershell / the command line."
sidebar: p_enterprise_sidebar
permalink: enterprise_commandline_userlevelaccess.html
folder: SpotlightEnterprise
---



## Manage access to Spotlight connections commands

### Get-Users

Fetch users from "Spotlight Diagnostic Administrators", "Spotlight Diagnostic Users" and "Spotlight Diagnostic Read-Only Users" groups.

Command parameters

Parameter | Use
----------|----
-DS | DS address, case insensitive.
-User | User Name, Separate each user with a comma, fuzzy matching and case insensitive.
-Role | Role Name, Separate each Role with a comma, fuzzy matching and case insensitive.


Get all users or specific user

```
Get-Users
```

```
Get-Users -DS f1-w10-tvm01.melquest.dev.mel.au.qsft -Role ADMIN -User user
```

### Get-Permission

Get allowed or denied connections from DS(s). By default this command does not show admin users.

Command parameters

Parameter | Use
----------|----
-DS | DS address, case insensitive.
-User | User name, separate each user with a comma. The user name supports fuzzy matching and is case insensitive.
-DisplayName | Connection display name, separate each display name with a comma, fuzzy matching and case insensitive.
-Technology | Technology name, separate each technology name with a comma, case insensitive.
-Tag | Connection tag name, separate each tag with a comma. The matching allows fuzzy matching when one tag is supplied but is always full matching when multiple tags are supplied. The matching is always case insensitive.
-Denied | Display only the denied connections for the user(s).


```
Get-Permission -DS dsserver1.contoso.com -User contoso\user1 -DisplayName sqlserver1 -Technology sqlserver -Tag prod
```

```
Get-Permission -User contoso\user1,user2 -DisplayName sqlserver1,winserver1 -Tag prod,NewYork -Denied
```

### Grant-Permission

Grant user access permission to connection(s).

Command parameters

Parameter | Use
----------|----
-DS | DS address, case-insensitive.
-User | User Name, separate each user with a comma, fuzzy matching and case insensitive.
-ConnectionName | The connection name will take the form of the address followed by the connection type, as in address_connectionType, separate each name with a comma, case insensitive.


Grant multiple connection permissions to one user.

```
Grant-Permission -User contoso\user1 -ConnectionName sqlserver1_replication,sqlserver1_sqlserver
```

Grant permission using the Get-Permission command in a pipeline.

```
Get-Permission -User contoso\user1,user2 -Denied -Technology sqlserver | Grant-Permission
```


### Revoke-Permission

Revoke the user access permission from connection(s).

Command parameters

Parameter | Use
----------|----
-DS | DS address, case insensitive.
-User | User Name, separate each user with a comma, fuzzy matching and case insensitive.
-ConnectionName | Connection technology name, separate each name with a comma, case insensitive.


Revoke multiple connection permissions for one user.

```
Revoke-Permission -User contoso\user1 -ConnectionName winserver1,sqlserver1_sqlserver
```

Revoke permission using the Get-Permission command in a pipeline.

```
Get-Permission -User contoso\user1,user2 -ConnectionName winserver1,sqlserver1_sqlserver | Revoke-Permission
```

{% include links.html %}
