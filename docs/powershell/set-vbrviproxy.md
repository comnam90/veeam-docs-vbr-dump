---
title: "Set-VBRViProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrviproxy.html"
last_updated: "4/18/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViProxy


Short Description

Modifies a VMware backup proxy.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViProxy -Proxy <CViProxy> [-TransportMode <VBRProxyTransportMode> {Auto | DirectStorageAccess | HotAdd | Nbd}] [-ConnectedDatastoreMode <VBRProxyConnectedDatastoreMode> {Auto | Manual}] [-Datastore <VBRViDatastore[]>] [-EnableFailoverToNBD] [-EnableHostToProxyEncryption] [-Description <string>] [-MaxTasks <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the selected VMware backup proxy server.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of VMware proxies you want to modify. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies a description of a VMware proxy. | String | False | Named | False |
| MaxTasks | Specifies the number of concurrent tasks that can be assigned to a proxy simultaneously.  Allowed values: 1-100.  Default: 2. | Int32 | False | Named | False |
| TransportMode | Specifies the transport mode used by a backup proxy:   * Auto: Use this option to set the automatic proxy selection mode. * DirectStorageAccess: Use this option to set the direct storage access transport mode (Direct SAN access or Direct NFS access). * HotAdd: Use this option to set the virtual appliance transport mode. * Nbd: Use this option to set the network transport mode.   Default: Auto. | VBRProxyTransportMode | False | Named | False |
| ConnectedDatastoreMode | Specifies the mode that a proxy will use to connect to datastores:   * Auto: Veeam Backup & Replication automatically detects all datastores that allow direct SAN or NFS connection.  * Manual: backup proxy has a direct SAN or NFS connection to datastores in the Datastore list. Use the Datastore parameter to specify the allowed datastores.   Default: Auto. | VBRProxyConnectedDatastoreMode | False | Named | False |
| Datastore | Specifies a list of datastores to which a backup proxy has a direct SAN or NFS connection. | Accepts the VBRViDatastore[] object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| EnableFailoverToNBD | Enables failover to the Network transport mode if a backup proxy fails to transport data using the Direct storage access or Virtual appliance transport mode.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableHostToProxyEncryption | Enables a VM data transportation over an encrypted SSL connection in the Network transport mode.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CViProxy[] that contains an array of VMware backup proxy servers added to the backup infrastructure.

Examples

Modifying VMware Backup Proxy

This example shows how to modify the VMware backup proxy named LocalProxy.

|  |
| --- |
| $proxy = Get-VBRViProxy -Name "LocalProxy"  Set-VBRViProxy -Proxy $proxy -TransportMode HotAdd -EnableFailoverToNBD |

Perform the following steps:

1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
2. Run the Set-VBRViProxy cmdlet. Set the $proxy variable as the Proxy parameter value. Set the HotAdd option for the TransportMode parameter. Provide the EnableFailoverToNBD parameter.

Related Commands

[Get-VBRViProxy](get-vbrviproxy.md)


