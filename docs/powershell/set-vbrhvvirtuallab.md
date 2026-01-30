---
title: "Set-VBRHvVirtualLab"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvvirtuallab.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvVirtualLab


Short Description

Modifies settings of Hyper-V virtual labs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvVirtualLab -VirtualLab <VBRHvVirtualLabConfiguration> [-Description <string>] [-Type {Simple | Advanced}] [-Path <string>] [-EnableProxyAppliance] [-ProxyAppliance <VBRHvVirtualLabProxyAppliance>] [-IsolatedNetworkOptions <VBRHvIsolatedNetworkOptions[]>] [-EnableRoutingBetweenNics] [-EnableStaticIPMapping] [-StaticIPMappingRule <VBRHvVirtualLabStaticIPMappingRule[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Hyper-V virtual labs of the following types:

* Hyper-V Basic Virtual Lab.
* Hyper-V Advanced Virtual Lab.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies a virtual lab that you want to modify. | Accepts the VBRHvVirtualLabConfiguration object. To get this object, run the [Get-VBRHvVirtualLabConfiguration](get-vbrhvvirtuallabconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies a description. The cmdlet will create a virtual lab with this description. | String | False | Named | False |
| Type | Specifies a networking mode for a virtual lab. You can select one of the following networking modes:   * Simple: use this option if all VMs that you want to verify are connected to the same production network.  * Advanced: use this option if all VMs that you want to verify are connected to different networks. | VBRHvVirtualLabType | False | Named | False |
| Path | Specifies the path to the folder where virtual lab will be stored. | String | False | Named | False |
| EnableProxyAppliance | Defines that the cmdlet will enable the proxy appliance option.  If you specify this option, Veeam Backup & Replication enable automatic recovery verification of VMs. Otherwise, Veeam Backup & Replication will only start VMs in the virtual lab and perform the heartbeat test for VMs during recovery verification. | SwitchParamter | False | Named | False |
| ProxyAppliance | Specifies a proxy appliance. The cmdlet will add this proxy appliance to a virtual lab. | Accepts the VBRHvVirtualLabProxyAppliance object. To get this object, run the [New-VBRHvVirtualLabProxyAppliance](new-vbrhvvirtuallabproxyappliance.md) cmdlet. | False | Named | False |
| IsolatedNetworkOptions | Specifies network settings of an isolated network. The cmdlet will create a virtual lab with the specified network settings. | Accepts the VBRHvIsolatedNetworkOptions[] object. To get this object, run the [New-VBRHvIsolatedNetworkOptions](new-vbrhvisolatednetworkoptions.md) cmdlet. | False | Named | False |
| EnableRoutingBetweenNics | Defines that the cmdlet will enable communication between isolated networks.  If you provide this parameter, the cmdlet will enable communication between isolated networks. Otherwise, Veeam Backup & Replication will not be able to connect the isolated networks with production networks. | SwitchParamter | False | Named | False |
| EnableStaticIPMapping | Defines that the cmdlet will enable the static IP mapping option.  If you provide this parameter, Veeam Backup & Replication will assign a static IP address to every VM in the virtual lab. Otherwise, you must update the routing table on every client machine. | SwitchParamter | False | Named | False |
| StaticIPMappingRule | Specifies static IP address mapping rules. The cmdlet will create a virtual lab with the specified mapping rules. | Accepts the VBRHvVirtualLabStaticIPMappingRule[] object. To get this object, run the [New-VBRHvVirtualLabStaticIPMappingRule](new-vbrhvvirtuallabstaticipmappingrule.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will not show any warning about network mapping. If you do not provide this parameter, the cmdlet will display a warning. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVirtualLabConfig[] object that contains settings of Hyper-V virtual labs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Virtual Lab Description

|  |  |
| --- | --- |
| This example shows how to modify description for the virtual lab named SQL Virtual Lab.  |  | | --- | | $lab = Get-VBRHvVirtualLabConfiguration -Name "SQL Virtual Lab"  Set-VBRHvVirtualLab -VirtualLab $lab -Description "Virtual Lab for SQL" |  Perform the following steps:   1. Run the [Get-VBRHvVirtualLabConfiguration](get-vbrhvvirtuallabconfiguration.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the Set-VBRHvVirtualLab cmdlet. Set the $lab variable as the VirtualLab parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Networking Mode for Virtual Lab

|  |  |
| --- | --- |
| This example shows how to modify networking mode for a virtual lab.  |  | | --- | | $lab = Get-VBRHvVirtualLabConfiguration -Name "SQL Virtual Lab"  Set-VBRHvVirtualLab -VirtualLab $lab -Type Advanced |  Perform the following steps:   1. Run the [Get-VBRHvVirtualLabConfiguration](get-vbrhvvirtuallabconfiguration.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the Set-VBRHvVirtualLab cmdlet. Set the $lab variable as the VirtualLab parameter value. Set the Advanced option for the Type parameter. |

Related Commands

[Get-VBRHvVirtualLabConfiguration](get-vbrhvvirtuallabconfiguration.md)


