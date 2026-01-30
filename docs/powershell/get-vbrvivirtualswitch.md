---
title: "Get-VBRViVirtualSwitch"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvivirtualswitch.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRViVirtualSwitch


Short Description

Returns VMware virtual switches.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRViVirtualSwitch -Server <Object[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns VMware virtual switches that are created on a ESXi host or cluster.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi or ESXi host or cluster. The cmdlet will return the virtual switches created on this host or cluster. | Accepts the Object[] object. Run the [Get-VBRServer](get-vbrserver.md) cmdlet to get this object. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRViVirtualSwitch](vbrvivirtualswitch.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Switches Created on Selected Host

|  |  |
| --- | --- |
| This example shows how to get switches created on the host named ESXiHost.  |  | | --- | | $server = Get-VBRServer –Type ESXi -Name "ESXiHost"  Get-VBRViVirtualSwitch -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the ESXi option for the Type parameter. Specify the Name parameter values. Save it to the $server variable. 2. Run the Get-VBRViVirtualSwitch cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Switches Created on Selected VMware Cluster

|  |  |
| --- | --- |
| This example shows how to get switches created on the VMware cluster named vSAN.  |  | | --- | | $cluster = Find-VBRViEntity -Server ESXiHost -HostsAndClusters -Name vSAN  Get-VBRViVirtualSwitch -Server $cluster |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the ESXiHost option for the Server parameter. Provide the HostsAndClusters parameter. Specify the Name parameter value. Save it to the $cluster variable. 2. Run the Get-VBRViVirtualSwitch cmdlet. Set the $cluster variable as the Server parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)


