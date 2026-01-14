---
title: "Find-VSBVirtualLab (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vsbvirtuallab.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Find-VSBVirtualLab (obsolete)

In this article

Short Description

Looks for virtual labs created on the specified ESXi host.

|  |
| --- |
| ![Find-VSBVirtualLab (obsolete)](images/icon_note.webp) Note: |
| This cmdlet is deprecated and will be marked as obsolete in the future. It is recommended to re-write your scripts using the [Connect-VBRViVirtualLab](connect-vbrvivirtuallab.md) cmdlet. |

Applies to

Platform: VMware

For Hyper-V, run the [Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Find-VSBVirtualLab -Server <CHost> [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns virtual labs created on the specified ESXi host, both registered in Veeam Backup & Replication and not.

You can get the list of all VMware virtual labs on the specified ESXi host or look for instances directly by name.

Run the [Connect-VSBVirtualLab](connect-vsbvirtuallab.md) cmdlet to add the unregistered virtual labs to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the VMware host. The cmdlet will return virtual labs created on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the array of virtual lab names. The cmdlet will return virtual labs with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CVirtualLabDescriptor

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Labs on ESXi Hosts [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the list of all virtual labs located on the ESXi hosts.  |  | | --- | | Get-VBRServer -Type ESXi | Find-VSBVirtualLab |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type parameter value. 2. Pipe the cmdlet output to the Find-VSBVirtualLab cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Virtual Labs on ESXi Hosts [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the MailServer\_VLab virtual lab connected to the ESXiHost ESXi host.  |  | | --- | | Get-VBRServer -Name "ESXiHost" | Find-VSBVirtualLab -Name "MailServer\_VLab" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Find-VSBVirtualLab cmdlet. Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
