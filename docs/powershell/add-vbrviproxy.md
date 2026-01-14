---
title: "Add-VBRViProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrviproxy.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViProxy

In this article

Short Description

Adds a VMware backup proxy to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViProxy -Server <CHost> [-Description <string>] [-MaxTasks <int>] [-TransportMode <VBRProxyTransportMode> {Auto | DirectStorageAccess | HotAdd | Nbd}] [-ConnectedDatastoreMode <VBRProxyConnectedDatastoreMode> {Auto |Manual}] [-Datastore <VBRViDatastore[]>] [-EnableFailoverToNBD] [-EnableHostToProxyEncryption]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a VMware backup proxy server to the backup infrastructure.

When you add a proxy, you assign the role of the backup proxy to a Windows-based or Linux-based server that you add to the backup infrastructure. To add a new proxy, you must add the necessary server to the backup infrastructure beforehand.

Run the [Add-VBRWinServer](add-vbrwinserver.md) cmdlet to add a Microsoft Windows server the backup infrastructure.

Run the [Add-VBRLinux](add-vbrlinux.md) cmdlet to add a Linux server to the backup infrastructure.

Run the [Add-VBRHvProxy](add-vbrhvproxy.md) cmdlet to add Hyper-V backup proxies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a server that will act as a VMware backup proxy. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies the description of a VMware proxy. | String | False | Named | False |
| MaxTasks | Specifies the number of concurrent tasks that can be assigned to a proxy simultaneously.  Permitted values: 1-100.  Default: 2. | Int32 | False | Named | False |
| TransportMode | Specifies the transport mode used by a backup proxy:   * Auto: Use this option to set the automatic proxy selection mode. * DirectStorageAccess: Use this option to set the direct storage access transport mode (Direct SAN access or Direct NFS access). * HotAdd: Use this option to set the virtual appliance transport mode. * Nbd: Use this option to set the network transport mode.   Default: Auto. | VBRProxyTransportMode | False | Named | False |
| ConnectedDatastoreMode | Specifies the mode a proxy will use to connect to datastores:   * Auto: Veeam Backup & Replication automatically detects all datastores that allow direct SAN or NFS connection.  * Manual: A backup proxy has a direct SAN or NFS connection to the datastores. Use the Datastore parameter to specify the allowed datastores.   Default: Auto. | VBRProxyConnectedDatastoreMode | False | Named | False |
| Datastore | Specifies a list of datastores to which a backup proxy has a direct SAN or NFS connection. | Accepts the VBRViDatastore [] object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| EnableFailoverToNBD | Enables failover to the Network transport mode if a backup proxy fails to transport data using the Direct storage access or Virtual appliance transport mode.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableHostToProxyEncryption | Enables VM data transportation over an encrypted SSL connection in the Network transport mode.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CViProxy[] that contains an array of VMware backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New VMware Backup Proxy [Using Variable]

|  |  |
| --- | --- |
| This example shows how to add a new VMware backup proxy. The description of the proxy is Local Backup Proxy. The max concurrent tasks number is set to 2 by default.  |  | | --- | | $server = Get-VBRServer -Name "VMware Local Server"  Add-VBRViProxy -Server $server -Description "Local Backup Proxy" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRViProxy cmdlet. Set the $server variable as the Server parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New VMware Backup Proxy [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to add a new VMware backup proxy. The description is Local Backup Proxy. The max concurrent tasks number is set to 6.  |  | | --- | | Get-VBRServer -Name "VMware Local Server" | Add-VBRViProxy -Description "Local Backup Proxy" -MaxTasks 6 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VBRViProxy cmdlet. Specify the Description parameter value. Specify the MaxTasks parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding New VMware Backup Proxy with Virtual Appliance Transport Mode

|  |  |
| --- | --- |
| This example shows how to add a new VMware backup proxy with the Virtual appliance transport mode. The failover to the network transport mode option is disabled.  |  | | --- | | $server = Get-VBRServer -Name "VMware Local Server"  Add-VBRViProxy -Server $server -Description "Local Backup Proxy" -TransportMode HotAdd -EnableFailoverToNBD:$false |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRViProxy cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value.  * Specify the Description parameter value.  * Set the HotAdd option for the TransportMode parameter.  * Set the EnableFailoverToNBD parameter to $false. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
