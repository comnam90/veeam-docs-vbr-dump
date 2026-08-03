---
title: "Get-VBRViVM"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvivm.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRViVM


Short Description

Returns VMs available on a vCenter Server.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get VMs by name.

|  |
| --- |
| Get-VBRViVM -Server <CHost> [-Name <String[]>] [<CommonParameters>] |

* Get VMs by reference.

|  |
| --- |
| Get-VBRViVM -Server <CHost> [-Reference <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns VMs available on a vCenter Server. Use this cmdlet to get VMs that will be used for mapping in a universal CDP policy.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Server | Specifies a vCenter Server. The cmdlet will return VMs available on this server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies an array of VM names. The cmdlet will return VMs with these names. | String[] | False | Named | False |
| Reference | Specifies an array of references (MoRefs) for VMs. The cmdlet will return VMs with these references. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns an array of [VBRViVM](vbrvivm.md) objects that contain VMware VMs available on the specified vCenter Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All VMs Available on vCenter Server

|  |  |
| --- | --- |
| This example shows how to get all VMs available on the vcenter01.tech.local vCenter Server.  |  | | --- | | $server = Get-VBRServer -Name "vcenter01.tech.local"  Get-VBRViVM -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRViVM cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VMs Available on vCenter Server by Names

|  |  |
| --- | --- |
| This example shows how to get the WebSrv01 and WebSrv02 VMs available on the vcenter01.tech.local vCenter Server.  |  | | --- | | $server = Get-VBRServer -Name "vcenter01.tech.local"  Get-VBRViVM -Server $server -Name "WebSrv01", "WebSrv02" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRViVM cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting VMs Available on vCenter Server by References

|  |  |
| --- | --- |
| This example shows how to get VMs with the vm-1024 and vm-1025 references available on the vcenter01.tech.local vCenter Server.  |  | | --- | | $server = Get-VBRServer -Name "vcenter01.tech.local"  Get-VBRViVM -Server $server -Reference "vm-1024", "vm-1025" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRViVM cmdlet. Set the $server variable as the Server parameter value. Specify the Reference parameter values. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)

Page updated 2026-05-27

