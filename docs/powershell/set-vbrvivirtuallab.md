---
title: "Set-VBRViVirtualLab"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvivirtuallab.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViVirtualLab


Short Description

Modifies settings of VMware virtual labs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViVirtualLab -VirtualLab <VBRViVirtualLabConfiguration> [-Type <VBRViVirtualLabType> {Simple | Advanced |AdvancedMultiHost}] [-Description <string>] [-EnableCacheRedirect] [-CacheDatastore <VBRViDatastore>] [-EnableProxyAppliance] [-ProxyAppliance <VBRViVirtualLabProxyAppliance>] [-DVS <VBRViVirtualSwitch>] [-NetworkMappingRule <VBRViVirtualLabNetworkMappingRule[]>] [-NetworkOptions <VBRViVirtualLabNetworkOptions[]>] [-EnableRoutingBetweenvNics] [-EnableStaticIPMapping] [-IpMappingRule <VBRViVirtualLabIPMappingRule[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of VMware virtual labs of the following kinds:

* VMware Basic Virtual Lab
* VMware Advanced Virtual Lab

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies a virtual lab that you want to modify. | Accepts the VBRViVirtualLabConfiguration object. To get this object, run the [Get-VBRViVirtualLabConfiguration](get-vbrvivirtuallabconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| Type | Specifies a networking mode for a virtual lab. You can select one of the following networking modes:   * Simple: use this option if all VMs that you want to verify are connected to the same production network. * Advanced: use this option if all VMs that you want to verify are connected to different networks and are located on the same ESXi hosts. * AdvancedMultiHost: use this option if all VMs that you want to verify are connected to different networks and are located on the different ESXi hosts. | VBRViVirtualLabType | False | Named | False |
| Description | Specifies a description. The cmdlet will create a virtual lab with this description. | String | False | Named | False |
| EnableCacheRedirect | Defines that the cmdlet will redirect redo logs of verified VMs to the datastore.  If you provide this parameter, Veeam Backup & Replication will keep the redo logs on the specified datastore. Otherwise, it will keep them on the vPower NFS server.  Run the CacheDatastore parameter to specify the datastore for the redo logs. | SwitchParamter | False | Named | False |
| CacheDatastore | Specifies a datastore to keep redo logs for verified VMs. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| EnableProxyAppliance | Defines that the cmdlet will enable the proxy appliance option.  If you specify this option, Veeam Backup & Replication enable automatic recovery verification of VMs. Otherwise, Veeam Backup & Replication will only start VMs in the virtual lab and perform the heartbeat test for VMs during recovery verification. | SwitchParamter | False | Named | False |
| ProxyAppliance | Specifies a proxy appliance. The cmdlet will add this proxy appliance to a virtual lab. | Accepts the VBRViVirtualLabProxyAppliance object. To get this object, run the [New-VBRViVirtualLabProxyAppliance](new-vbrvivirtuallabproxyappliance.md) cmdlet. | False | Named | False |
| DVS | Specifies the VMware Distributed vSwitch. The create a virtual lab with the specified virtual switch. | Accepts the VBRViVirtualSwitch object. To get this object, run the [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) cmdlet. | False | Named | False |
| NetworkMappingRule | Specifies mapping rules of isolated networks with production networks. The cmdlet will create a virtual lab with the specified mapping rules. | Accepts the VBRViVirtualLabNetworkMappingRule[] object. To get this object, run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. | False | Named | False |
| NetworkOptions | Specifies network settings of an isolated network. The cmdlet will create a virtual lab with the specified network settings. | Accepts the VBRViVirtualLabNetworkOptions[] object. To get this object, run the [New-VBRViVirtualLabNetworkOptions](new-vbrvivirtuallabnetworkoptions.md) cmdlet. | False | Named | False |
| EnableRoutingBetweenvNics | Defines that the cmdlet will enable communication between isolated networks.  If you provide this parameter, the cmdlet will enable communication between isolated networks. Otherwise, Veeam Backup & Replication will not be able to connect the isolated networks with production networks. | SwitchParamter | False | Named | False |
| EnableStaticIPMapping | Defines that the cmdlet will enable the static IP mapping option.  If you provide this parameter, Veeam Backup & Replication will assign a static IP address to every VM in the virtual lab. Otherwise, you must update the routing table on every client machine. | SwitchParamter | False | Named | False |
| IpMappingRule | Specifies static IP address mapping rules. The cmdlet will create a virtual lab with the specified mapping rules. | Accepts the VBRViVirtualLabIPMappingRule[] object. To get this object, run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will not show any warning about network mapping. If you do not provide this parameter, the cmdlet will display a warning. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualLabConfig>[] object that contains settings of basic VMware virtual labs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Datastore for Virtual Lab

|  |  |
| --- | --- |
| This example shows how to specify the custom datastore for a virtual lab. Veeam Backup & Replication will keep redo logs on the esx09-das6 datastore instead of the Power NFS server.  |  | | --- | | $lab = Get-VBRViVirtualLabConfiguration -Name "SQL Virtual Lab"  $ESXi = Get-VBRServer -Name "esx09.tech.local"  $datastore = Find-VBRViDatastore -Server $ESXi -Name "esx09-das6"  Set-VBRViVirtualLab -VirtualLab $lab -CacheDatastore $datastore |  Perform the following steps:   1. Run the [Get-VBRViVirtualLabConfiguration](get-vbrvivirtuallabconfiguration.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $ESXi variable. 3. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $ESXi as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable. 4. Run the Set-VBRViVirtualLab cmdlet. Set the $lab variable as the VirtualLab parameter value. Set the $datastore variable as the CacheDatastore parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Networking Mode for Virtual Lab

|  |  |
| --- | --- |
| This example shows how to modify networking mode for a virtual lab. The networking mode will be switched to verify that all VMs are connected to different networks and are located on the same ESXi hosts.  |  | | --- | | $lab = Get-VBRViVirtualLabConfiguration -Name "SQL Virtual Lab"  Set-VBRViVirtualLab -VirtualLab $lab -Type Advanced |  Perform the following steps:   1. Run the [Get-VBRViVirtualLabConfiguration](get-vbrvivirtuallabconfiguration.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the Set-VBRViVirtualLab cmdlet. Set the $lab variable as the VirtualLab parameter value. Set the Advanced option for the Type parameter. |

Related Commands

* [Get-VBRViVirtualLabConfiguration](get-vbrvivirtuallabconfiguration.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Get-VBRServer](get-vbrserver.md)


