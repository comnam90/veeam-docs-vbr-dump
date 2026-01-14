---
title: "Find-VBRViEntity"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrvientity.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Find-VBRViEntity

In this article

Short Description

Looks for VMware objects.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for VMware hosts and clusters.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-HostsAndClusters]  [<CommonParameters>] |

* Look for VMware VMs, templates and folders.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-VMsAndTemplates]  [<CommonParameters>] |

* Look for VMware datastores and VMs.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-DatastoresAndVMs]  [<CommonParameters>] |

* Look for VMware hosts and datastores.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-HostsAndDatastores]  [<CommonParameters>] |

* Look for VMware resource pools.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-ResourcePools]  [<CommonParameters>] |

* Look for VMware servers.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-Servers]  [<CommonParameters>] |

* Look for VMware tags.

|  |
| --- |
| Find-VBRViEntity [-Name <String[]>] [-Server <CHost[]>] [-Tags]  [<CommonParameters>] |

Detailed Description

This cmdlet returns VMware objects connected to a specified ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of VMware object names. The cmdlet will return entities with these names. | String[] | False | Named | True |
| Server | Specifies an array of ESXi hosts. The cmdlet will return entities created on these hosts. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, |
| HostsAndClusters | Defines that the cmdlet will return only hosts and clusters.  Default: False. | SwitchParameter | False | Named | False |
| VMsAndTemplates | Defines that the cmdlet will return only VMs, folders and templates. | SwitchParameter | False | Named | False |
| DatastoresAndVMs | Defines that the cmdlet will return only datastores and VMs.  Default: False. | SwitchParameter | False | Named | False |
| HostsAndDatastores | Defines that the cmdlet will return only hosts and datastores.  Default: False. | SwitchParameter | False | Named | False |
| ResourcePools | Defines that the cmdlet will return only resource pools.  Default: False. | SwitchParameter | False | Named | False |
| Servers | Defines that the cmdlet will return only VMware hosts.  Default: False. | SwitchParameter | False | Named | False |
| Tags | Defines that the cmdlet will return only tags.  Default: False.  Note:   * To get the necessary tags of the VMware objects, you must specify the vCenter Server in the Server parameter. If you specify ESXi hosts, the cmdlet will not return any data. If you don't provide the Server parameter, the cmdlet will return tags for all servers, added to a backup infrastructure. * To specify the tag name, use the Name parameter. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the following VMware objects connected to a specified ESXi host:

* CVcItem
* CViFolderItem
* CViDatacenterItem
* CEsxItem
* CViClusterItem
* CViResourcePoolItem
* CViVmItem
* CViVirtualAppItem
* CViTagItem

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Hosts and Clusters Connected to Specific ESXI Hosts

|  |  |
| --- | --- |
| This example shows how to get a list of hosts and clusters that are connected to the following ESXi hosts: ESXiHost 01 and ESXiHost 02.  |  | | --- | | $server = Get-VBRServer -Name "ESXiHost 01", "ESXiHost 02"  Find-VBRViEntity -HostsAndClusters -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRViEntity cmdlet. Provide the HostsAndClusters parameter. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Cluster from ESXI Host

|  |  |
| --- | --- |
| This example shows how to get the vSAN ESXi cluster named located on the ESX01 ESXiHost.  |  | | --- | | $server = Get-VBRServer -Name "ESX01"  Find-VBRViEntity -Server $server -HostsAndClusters -Name vSAN |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRViEntity cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Provide the HostsAndClusters parameter. * Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting List of Resource Pools

|  |  |
| --- | --- |
| This example shows how to get a list of resource pools with names starting with Veeam. The resource pools are located on the ESX01 ESXi host.  |  | | --- | | $server = Get-VBRServer -Name "ESX01"  Find-VBRViEntity -Server $server -ResourcePools -Name Veeam\* |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRViEntity cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Provide the ResourcePools parameter. * Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting List of VMware Tags

|  |  |
| --- | --- |
| This example shows how to get a list of the Mac OS VMware tags within the vcenter05.tech.global vCenter.  |  | | --- | | $server = Get-VBRServer -Name vcenter05.tech.global  Find-VBRViEntity -Server $server -Tags -Name "Mac OS" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRViEntity cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Provide the Tags parameter. * Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
