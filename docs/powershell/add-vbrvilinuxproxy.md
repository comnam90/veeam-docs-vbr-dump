---
title: "Add-VBRViLinuxProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvilinuxproxy.html"
last_updated: "4/3/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViLinuxProxy

In this article

Short Description

Adds Linux backup proxies to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViLinuxProxy -Server <CHost> [-Description <String>] [-MaxTasks <Int32>] [-ProxyVM <CViVmItem>] [-TransportMode <VBRProxyTransportMode>] [-ConnectedDatastoreMode <VBRProxyConnectedDatastoreMode>] [-Datastore <VBRViDatastore[]>] [-EnableFailoverToNBD] [-EnableHostToProxyEncryption] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Linux backup proxies to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Linux VM which will act as a backup proxy. The cmdlet will assign a role of a backup proxy to the Linux server that is added to the backup infrastructure.  Note: You must provide the ProxyVM parameter in the following cases:   * If Veeam Backup & Replication can not get the BIOS UUID of the Linux VM that you want to add as a backup proxy. * If the disk.EnableUUID parameter in the vSphere configuration settings is set to False for the Linux VM that you want to add as a backup proxy. * If the Linux VM that you want to add as a backup proxy has been cloned or converted and this duplicate VM has the same BIOS UUID as the original one. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies the description of the Linux backup proxy. | String | False | Named | False |
| MaxTasks | Specifies the number of concurrent tasks that can be assigned to the backup proxy simultaneously.  Permitted values: 1-100.  Default: 2. | Int32 | False | Named | False |
| ProxyVM | Specifies a Linux VM that is added to the VMware environment. The cmdlet will assign a backup proxy role explicitly to this Linux VM. | Accepts the CViVmItem object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| TransportMode | Specifies a data transport mode that the Linux proxy will apply to retrieve VM data from the source and write VM data to the target. You can specify one of the following transport mode type:  Specifies the transport mode used by the backup proxy:   * Auto: Use this option to set the automatic proxy selection mode. * DirectStorageAccess: Use this option to set the direct storage access transport mode (Direct SAN access or Direct NFS access). * HotAdd: Use this option to set the virtual appliance transport mode. * Nbd: Use this option to set the network transport mode.   Default: Auto. | VBRProxyTransportMode | False | Named | False |
| ConnectedDatastoreMode | Specifies the mode the Linux proxy will use to connect to datastores:   * Auto: Veeam Backup & Replication automatically detects all datastores that allow direct SAN or NFS connection. * Manual: Backup proxy has a direct SAN or NFS connection to datastores in the Datastore list. Use the Datastore parameter to specify the allowed datastores.   Default: Auto. | VBRProxyConnectedDatastoreMode | False | Named | False |
| Datastore | Specifies an array of datastores to which the backup proxy has a direct SAN or NFS connection. | Accepts the VBRViDatastore [] object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| EnableFailoverToNBD | Enables failover to the Network transport mode if a backup proxy fails to transport data using the Direct storage access or Virtual appliance transport mode.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableHostToProxyEncryption | Enables VM data transportation over an encrypted SSL connection in the Network transport mode.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add a Linux backup proxy without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvServerVolume object that contains settings of Linux backup proxy added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Linux Backup Proxy

|  |  |
| --- | --- |
| This example shows how to add the LinSrv2045 VM as a Linux backup proxy to the infrastructure. The backup proxy is assigned 3 maximum concurrent tasks.  |  | | --- | | $linuxsrv = Get-VBRServer -Name "LinSrv2045"  Add-VBRViLinuxProxy -Server $linuxsrv -MaxTasks 3 -Force |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $linuxsrv variable. 2. Run the Add-VBRViLinuxProxy cmdlet. Set the $linuxsrv variable as the Server parameter value. Specify the MaxTasks parameter value. Provide the Force parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Linux Backup Proxy and Assigning Backup Proxy Role Explicitly

|  |  |
| --- | --- |
| This example shows how to add a Linux backup proxy to the backup infrastructure. The backup proxy will be configured with 2 maximum concurrent tasks.  |  | | --- | | $linuxsrv = Get-VBRServer -Name "LinSrv2045"  $proxy = Find-VBRViEntity -Name "LinSrv2045"  Add-VBRViLinuxProxy -Server $linuxsrv -ProxyVM $proxy -Force |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $linuxsrv variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 3. Run the Add-VBRViLinuxProxy cmdlet. Specify the following settings:  * Set the $linuxsrv variable as the Server parameter value. * Set the $proxy variable as the ProxyVM parameter value. * Provide the Force parameter. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)

Page updated 4/3/2024

Page content applies to build 13.0.1.1071
