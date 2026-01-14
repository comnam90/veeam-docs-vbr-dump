---
title: "Set-VBRViLinuxProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvilinuxproxy.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViLinuxProxy

In this article

Short Description

Modifies settings of Linux backup proxies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViLinuxProxy -Proxy <CViProxy> [-Description <string>] [-ProxyVM <CViVmItem>] [-TransportMode {Auto | DirectStorageAccess | HotAdd | Nbd}] [-ConnectedDatastoreMode {Auto | Manual}] [-Datastore <VBRViDatastore[]>] [-EnableFailoverToNBD] [-EnableHostToProxyEncryption] [-MaxTasks <int>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Linux backup proxy servers.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies a Linux backup proxy. The cmdlet will modify the settings of this backup proxy. | Accepts the CViProxy object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description of a Linux backup proxy. | String | False | Named | False |
| ProxyVM | Specifies a Linux VM that is added to the VMware environment. The cmdlet will assign a backup proxy role explicitly to this Linux VM. | Accepts the CViVmItem object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| TransportMode | Specifies a data transport mode that the Linux proxy will apply to retrieve VM data from the source and write VM data to the target. You can specify one of the following transport mode type:  Specifies the transport mode used by the backup proxy:   * Auto: Use this option to set the automatic proxy selection mode. * DirectStorageAccess: Use this option to set the direct storage access transport mode (Direct SAN access or Direct NFS access). * HotAdd: Use this option to set the virtual appliance transport mode. * Nbd: Use this option to set the network transport mode.   Default: Auto. | VBRProxyTransportMode | False | Named | False |
| ConnectedDatastoreMode | Specifies the mode the Linux proxy will use to connect to datastores:   * Auto: Veeam Backup & Replication automatically detects all datastores that allow direct SAN or NFS connection.  * Manual: Backup proxy has a direct SAN or NFS connection to datastores in the Datastore list. Use the Datastore parameter to specify the allowed datastores.   Default: Auto. | VBRProxyConnectedDatastoreMode | False | Named | False |
| Datastore | Specifies an array of datastores to which the backup proxy has a direct SAN or NFS connection. | Accepts the VBRViDatastore [] object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| EnableFailoverToNBD | Enables failover to the Network transport mode if a backup proxy fails to transport data using the Direct storage access or Virtual appliance transport mode.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableHostToProxyEncryption | Enables VM data transportation over an encrypted SSL connection in the Network transport mode.  Default: False. | SwitchParameter | False | Named | False |
| MaxTasks | Specifies the number of concurrent tasks that can be assigned to the backup proxy simultaneously.  Permitted values: 1-100.  Default: 2. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will add a Linux backup proxy without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvServerVolume object that contains settings of Linux backup proxy added to the backup infrastructure.

Examples

Modifying Number of Concurrent Tasks

This example shows how to modify a number of concurrent tasks for the Linux server.

|  |
| --- |
| $proxy = Get-VBRViProxy -Name "LinProxy"  Set-VBRViLinuxProxy -Proxy $proxy -MaxTasks 4 |

Perform the following steps:

1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
2. Run the Set-VBRViLinuxProxy cmdlet. Set the $proxy variable as the Proxy parameter value. Specify the MaxTasks parameter value.

Related Commands

[Get-VBRViProxy](get-vbrviproxy.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
