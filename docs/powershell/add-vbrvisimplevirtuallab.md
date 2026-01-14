---
title: "Add-VBRViSimpleVirtualLab"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvisimplevirtuallab.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViSimpleVirtualLab

In this article

Short Description

Creates a VMware basic virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViSimpleVirtualLab -Server <CHost> [-Name <string>] [-Description <string>] [-DesignatedResourcePoolName <string>] [-DesignatedVMFolderName <string>] [-CacheDatastore <VBRViDatastore>] [-ProxyAppliance <VBRViVirtualLabProxyAppliance>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VMware basic virtual lab.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an ESXi host. The cmdlet will create a virtual lab on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Name | Specifies a name. The cmdlet will create a virtual lab with this name. | String | False | Named | False |
| Description | Specifies a description. The cmdlet will create a virtual lab with this description. | String | False | Named | False |
| DesignatedResourcePoolName | Specifies a name of a resource pool. The cmdlet will create the resource pool with the specified name on the ESXi host.  Default: Same name as the virtual lab. | String | False | Named | False |
| DesignatedVMFolderName | Specifies a name of the dedicated folder. The cmdlet will create the folder in a resource pool with the specified name.  Default: Same name as the virtual lab. | String | False | Named | False |
| CacheDatastore | Specifies a datastore to keep redo logs for verified VMs.  Note: If you do not specify this parameter, Veeam Backup & Replication will store redo logs on the vPower NFS server. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| ProxyAppliance | Specifies a proxy appliance. The cmdlet will add this proxy appliance to a virtual lab. | Accepts the VBRViVirtualLabProxyAppliance object. To get this object, run the [New-VBRViVirtualLabProxyAppliance](new-vbrvivirtuallabproxyappliance.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVirtualLab object that contains settings of basic VMware virtual labs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Basic Virtual Lab

|  |  |
| --- | --- |
| This example shows how to create a basic virtual lab with default settings. The cmdlet will create the virtual lab on the esx09.tech.local ESXi host.  |  | | --- | | $ESXi = Get-VBRServer -Name "esx09.tech.local"  Add-VBRViSimpleVirtualLab -Server $ESXi -Name "Exchange Lab" -Description "Virtual Lab for Exchange VMs" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $ESXi variable. 2. Run the Add-VBRViSimpleVirtualLab cmdlet. Set the $ESXi variable as the Server parameter value. Specify the Name parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Virtual Lab with Custom Datastore

|  |  |
| --- | --- |
| This example shows how to create a basic virtual lab with a custom datastore. The virtual lab will be created with the following settings:   * Veeam Backup & Replication will keep redo logs on the esx09-das6 datastore.  * The virtual lab will be located on the SQL test resource pool with the SQL folder.     |  | | --- | | $ESXi = Get-VBRServer -Name "esx09.tech.local"  $datastore = Find-VBRViDatastore -Server $ESXi -Name "esx09-das6"  Add-VBRViSimpleVirtualLab -Server $ESXi -Name "SQL Database Lab" -Description "Virtual Lab for SQL Databases" -DesignatedResourcePoolName "SQL test" -DesignatedVMFolderName "SQL" -CacheDatastore $datastore |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $ESXi variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $ESXi variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable. 3. Run the Add-VBRViSimpleVirtualLab cmdlet. Specify the following settings:  * Set the $ESXi variable as the Server parameter value. * Specify the Name parameter value. * Specify the Description parameter value. * Specify the DesignatedResourcePoolName parameter value. * Specify the DesignatedVMFolderName parameter value. * Set the $datastore variable as the CacheDatastore parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
