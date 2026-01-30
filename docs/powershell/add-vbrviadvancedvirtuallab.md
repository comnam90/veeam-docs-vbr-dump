---
title: "Add-VBRViAdvancedVirtualLab"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrviadvancedvirtuallab.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViAdvancedVirtualLab


Short Description

Creates a VMware advanced virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViAdvancedVirtualLab -Server <CHost> [-Name <string>] [-Description <string>] [-DesignatedResourcePoolName <string>] [-DesignatedVMFolderName <string>] [-CacheDatastore <VBRViDatastore>] [-ProxyAppliance <VBRViVirtualLabProxyAppliance>] [-NetworkMappingRule <VBRViVirtualLabNetworkMappingRule[]>] [-NetworkOptions <VBRViVirtualLabNetworkOptions[]>] [-EnableRoutingBetweenvNics] [-DVS <VBRViVirtualSwitch>] [-IpMappingRule<VBRViVirtualLabIPMappingRule[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VMware advanced virtual lab.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an ESXi host. The cmdlet will create a virtual lab on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Name | Specifies a name. The cmdlet will create a virtual lab with this name. | String | False | Named | False |
| Description | Specifies a description. The cmdlet will create a virtual lab with this description. | String | False | Named | False |
| DesignatedResourcePoolName | Specifies a name of a resource pool. The cmdlet will create the resource pool with the specified name on the ESXi host.  Default: Same name as the Virtual Lab. | String | False | Named | False |
| DesignatedVMFolderName | Specifies a name of the dedicated folder. The cmdlet will create the folder in a resource pool with the specified name.  Default: Same name as the Virtual Lab. | String | False | Named | False |
| CacheDatastore | Specifies a datastore to keep redo logs for verified VMs.  Note: If you do not specify this parameter, Veeam Backup & Replication will store redo logs on the vPower NFS server. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| ProxyAppliance | Specifies a proxy appliance. The cmdlet will add this proxy appliance to a virtual lab. | Accepts the VBRViVirtualLabProxyAppliance object. To get this object, run the [New-VBRViVirtualLabProxyAppliance](new-vbrvivirtuallabproxyappliance.md) cmdlet. | False | Named | False |
| NetworkMappingRule | Specifies mapping rules of isolated networks with production networks. The cmdlet will create a virtual lab with the specified mapping rules. | Accepts the VBRViVirtualLabNetworkMappingRule[] object. To get this object, run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. | False | Named | False |
| NetworkOptions | Specifies network settings of an isolated network. The cmdlet will create a virtual lab with the specified network settings. | Accepts the VBRViVirtualLabNetworkOptions[] object. To get this object, run the [New-VBRViVirtualLabNetworkOptions](new-vbrvivirtuallabnetworkoptions.md) cmdlet. | False | Named | False |
| EnableRoutingBetweenvNics | Defines that the cmdlet will enable communication between isolated networks.  If you provide this parameter, the cmdlet will enable communication between isolated networks. Otherwise, Veeam Backup & Replication will not be able to connect the isolated networks with production networks. | SwitchParamter | False | Named | False |
| DVS | Specifies the VMware Distributed vSwitch. The create a virtual lab with the specified virtual switch. | Accepts the VBRViVirtualSwitch object. To get this object, run the [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) cmdlet. | False | Named | False |
| IpMappingRule | Specifies static IP address mapping rules. The cmdlet will create a virtual lab with the specified mapping rules. | Accepts the VBRViVirtualLabIPMappingRule[] object. To get this object, run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will not show any warning about network mapping. If you do not provide this parameter, the cmdlet will display a warning. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVirtualLab object that contains settings of advanced VMware virtual labs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Advanced Virtual Lab

|  |  |
| --- | --- |
| This example shows how to create an advanced virtual lab with default settings. The cmdlet will create the virtual lab on the esx09.tech.local ESXi host.  |  | | --- | | $esxi = Get-VBRServer -Name "esx09.tech.local"  Add-VBRViAdvancedVirtualLab -Server $esxi -Name "Exchange Lab" -Description "Virtual Lab for Exchange VMs" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $esxi variable. 2. Run the Add-VBRViAdvancedVirtualLab cmdlet. Set the $esxi variable as the Server parameter value. Specify the Name parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Virtual Lab with Custom Datastore

|  |  |
| --- | --- |
| The following request returns license usage data for the VAO server with the ID 76da0d75-75b0-4675-8296-0142ad0d52a7.   * Veeam Backup & Replication will keep redo logs on the esx09-das6 datastore. * The virtual lab will be located on the SQL test resource pool with the SQL folder.     |  | | --- | | $esxi = Get-VBRServer -Name "esx09.tech.local"  $datastore = Find-VBRViDatastore -Server $esxi -Name "esx09-das6"  Add-VBRViAdvancedVirtualLab -Server $esxi -Name "SQL Database Lab" -Description "Virtual Lab for SQL Databases" -DesignatedResourcePoolName "SQL test" -DesignatedVMFolderName "SQL" -CacheDatastore $datastore |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $esxi variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $esxi variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable. 3. Run the Add-VBRViAdvancedVirtualLab cmdlet. Specify the following settings:  * Set the $esxi variable as the Server parameter value. * Specify the Name parameter value. * Specify the Description parameter value. * Specify the DesignatedResourcePoolName parameter value. * Specify the DesignatedVMFolderName parameter value. * Set the $datastore variable as the CacheDatastore parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)


