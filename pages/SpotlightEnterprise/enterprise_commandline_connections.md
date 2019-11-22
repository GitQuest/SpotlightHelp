---
title: Windows Powershell / Connections Command line 
summary: "List / edit / delete Spotlight Connections from Windows Powershell / the command line."
sidebar: p_enterprise_sidebar
permalink: enterprise_commandline_connections.html
folder: SpotlightEnterprise
---


## Basic commands

### List Spotlight connections

```
Get-Connection
```


### Delete a Spotlight connection

See also [Remove many connections](#RemoveManyConnections).

```
Remove-Connection -Name connectionName -PassThru
```



### Add a Spotlight connection

#### Windows authentication (using Diagnostic Server credentials)

See also [Add a list of connections](#AddAListOfConnections).

```
Add-Connection -Address address -Technology connectionType -Tag tag -Enabled -PassThru
```

#### Supply User / Password details

See also [Add a list of connections](#AddAListOfConnections).

```
Add-Connection -Credential $(get-credential) -Address address -Technology connectionType -Tag tag -Enabled -PassThru
```



### Change the authentication used to monitor a Spotlight connection

#### Supply User / Password details

```
Get-Connection -Name connectionName | Set-Connection -Credential $(get-credential)
```

#### Change to Windows authentication (using Diagnostic Server credentials)

```
Get-Connection -Name connectionName | Set-Connection -UseDSAuth
```

#### Update Tag (using Diagnostic Server credentials)

```
Get-Connection -Name connectionName | Set-Connection -Tag tag
```

### Disable monitoring a Spotlight connection

```
Get-Connection -Name connectionName | Set-Connection -Disabled
```

### Re-enable monitoring a Spotlight connection

```
Get-Connection -Name connectionName | Set-Connection -Enabled
```

## Windows Powershell / Command line parameters

### -Name connectionName

Supply the name of the connection.

{% include note.html content="The connection name is not user-assignable. When executing Add-Connection from the command line, the connection name will take the form of the address followed by the connection type, as in address_connectionType" %}

Connection names are not case sensitive.

{% include tip.html content="A list of connection names can be summarized by wildcards * and ? as per prefix* or \*infix\* or on?char." %}

### -Address address

Supply the address of the Spotlight connection as per the form of the address entered in the **Spotlight Client \| Configure Connections \| Properties \| Details \| Address field**. For example: the Server Name, Server Instance Name, or IP address.

### -Technology connectionType

Supply the connection type in Internet MIME format. For example: os/windows, os/vmware. More free form forms are accepted such as windows, vmware, hyperv, sqlserver, sqlazure, analysisservices, replication and availabilitygroups.

### -Tag tag

Supply the tag of the connection, not case sensitive, input one of tags or all of the tags, no need input the # sign.

### -Credential $(get-credential)

Use the -Credential parameter to specify User / Password details as per the connection type. For Add-Connection, where the -Credential parameter is not specified, Windows authentication (using Diagnostic Server credentials) is assumed.

The -Credential parameter requires a PSCredential object, which is a Powershell built-in object.

It can be used via a temporary variable (preferable if you want to add many connections) as per:

```
$c = $(get-credential)

Add-Connection -Credential $c -Technology sqlserver -Address my.host.name\instance -Enabled
```

It can be used inline as per:

```
Add-Connection -Credential $(get-credential) -Technology sqlserver -Address my.host.name\instance -Enabled
```

### -Enabled

Enable Spotlight monitoring on this connection.


### -Disabled


Disable Spotlight monitoring on this connection.


## Add a list of connections {#AddAListOfConnections}

Add a list of connections where all connections are of the same technology / connection type. Separate each address with a comma. Supply one technology type.

```
Add-Connection -Address address1,address2,address3 -Technology connectionType -Tag tag -Enabled -PassThru
```

Add a list of connections where there are varying connection types. Separate each address with a comma. Provide a list of technology types where the first address corresponds to the first technology type, the second address corresponds to the second technology type etc.

```
Add-Connection -Address address1,address2,address3 -Technology connectionType1,connectionType2,connectionType3 -Enabled -PassThru
```


## Remove many connections {#RemoveManyConnections}

Remove all connections

```
Remove-Connection -Name *
```


Remove all connections of a specific type (technology)

```
Remove-Connection -Technology connectionType
```

For example to remove all connections where the connection type is SQL Server:

```
Remove-Connection -Technology sqlserver
```

Remove a list of connections. Type the name of each connection. Separate each connection name with a comma.

```
Remove-Connection -Name connectionName1,connectionName2,connectionName3
```

Remove a list of connections where the connection names form a pattern.

```
Remove-Connection -Name connectionName*
```

For example to remove all connections where the name begins with the characters "address":

```
Remove-Connection -Name address*
```

{% include links.html %}
