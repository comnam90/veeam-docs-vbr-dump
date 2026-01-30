---
title: "Find-VBRHvEntity"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrhventity.html"
last_updated: "4/3/2024"
product_version: "13.0.1.1071"
---

# Find-VBRHvEntity


Short Description

Returns Hyper-V objects.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for an array of Hyper-V hosts and VMs.

|  |
| --- |
| Find-VBRHvEntity [-Name <String[]>] [-Server <CHost[]>] [-HostsAndVMs]  [<CommonParameters>] |

* Look for an array of Hyper-V hosts.

|  |
| --- |
| Find-VBRHvEntity [-Name <String[]>] [-Server <CHost[]>] [-Hosts]  [<CommonParameters>] |

* Look for an array of Hyper-V hosts and volumes.

|  |
| --- |
| Find-VBRHvEntity [-Name <String[]>] [-Server <CHost[]>] [-HostsAndVolumes]  [<CommonParameters>] |

* Look for an array of Hyper-V VM groups.

|  |
| --- |
| Find-VBRHvEntity [-Name <String[]>] [-Server <CHost[]>] [-VMGroups]  [<CommonParameters>] |

* Look for an array of Hyper-V tags:

|  |
| --- |
| Find-VBRHvEntity [-Name <String[]>] [-Server <CHost[]>] [-Tags]  [<CommonParameters>] |

Detailed Description

This cmdlet retutns an array of Hyper-V objects.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of entity names. The cmdlet will return entities with these names. | String[] | False | Named | False |
| Server | Specifies an array of Hyper-V hosts. The cmdlet will return entities created on these hosts. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, |
| HostsAndVMs | Defines that the cmdlet will return an array of hosts and VMs.  Default: False. | SwitchParameter | False | Named | False |
| Hosts | Defines that the cmdlet will return an array of hosts.  Default: False. | SwitchParameter | False | Named | False |
| HostsAndVolumes | Defines that the cmdlet will return an array of hosts and volumes.  Default: False. | SwitchParameter | False | Named | False |
| VMGroups | Defines that the cmdlet will return an array of VM groups.  Default: False. | SwitchParameter | False | Named | False |
| Tags | Defines that the cmdlet will return an array of tags.  Note: To specify the tag name, provide the Name parameter.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the following Hyper-V objects:

* CRootItem
* CHvHostItem
* CHvVmItem

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Hosts and VMs Available on Hyper-V

|  |  |
| --- | --- |
| This example shows how to get a list of all hosts and VMs available on the HvHost Hyper-V server.  |  | | --- | | $server = Get-VBRServer -Name "HvHost"  Find-VBRHvEntity -Server $server -HostsAndVMs |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRHvEntity cmdlet. Set the $server variable as the Server parameter value. Provide the HostsAndVMs parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting all Hosts Available on Hyper-V

|  |  |
| --- | --- |
| This example shows how to get a list of all hosts available on the HvHost Hyper-V server.  |  | | --- | | $server = Get-VBRServer -Name "HvHost"  Find-VBRHvEntity -Server $server -Hosts |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the Find-VBRHvEntity cmdlet. Set the $server variable as the Server parameter value. Provide the Hosts parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting all Hosts and Volumes Available on Hyper-V

|  |  |
| --- | --- |
| This example shows how to get a list of all hosts and volumes available on the HvHost Hyper-V server.  |  | | --- | | $server = Get-VBRServer -Name "HvHost"  Find-VBRHvEntity -Server $server -HostsAndVolumes |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the Find-VBRHvEntity cmdlet. Set the $server variable as the Server parameter value. Provide the HostsAndVolumes parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting all Hyper-V Tags

|  |  |
| --- | --- |
| This example shows how to get a list of all tags available on the HvHost Hyper-V server.  |  | | --- | | $server = Get-VBRServer -Name "HvHost"  Find-VBRHvEntity -Server $server -Tags |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the Find-VBRHvEntity cmdlet. Set the $server variable as the Server parameter value. Provide the Tags parameter. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


