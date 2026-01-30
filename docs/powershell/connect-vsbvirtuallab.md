---
title: "Connect-VSBVirtualLab (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vsbvirtuallab.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Connect-VSBVirtualLab (obsolete)


Short Description

Connects an existing VMware virtual lab.

|  |
| --- |
| ![Connect-VSBVirtualLab (obsolete)](images/icon_note.webp) Note: |
| This cmdlet is deprecated and will be marked as obsolete in the future. It is recommended to re-write your scripts using the [Connect-VBRViVirtualLab](connect-vbrvivirtuallab.md) cmdlet. |

Applies to

Platform: VMware

For Hyper-V, run the [Connect-VSBHvVirtualLab](connect-vsbhvvirtuallab.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VSBVirtualLab -VirtualLab <CVirtualLabDescriptor> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet connects an existing VMware virtual lab to Veeam Backup & Replication console.

When you add a new host to your Veeam Backup & Replication console, the virtual labs that are registered on it are not added automatically. Use this cmdlet to add the virtual labs to your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies the virtual lab you want to connect. | Accepts the CVirtualLabDescriptor object. To get this object, run the [Find-VSBVirtualLab](find-vsbvirtuallab.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Connecting Virtual Lab [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to connect the Exchange VLab 01 virtual lab to Veeam Backup & Replication.  |  | | --- | | $server = Get-VBRServer -Name "srv001"  Find-VSBVirtualLab -Server $server -Name "Exchange VLab 01" | Connect-VSBVirtualLab |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VSBVirtualLab](find-vsbvirtuallab.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. 3. Pipe the cmdlet output to the Connect-VSBVirtualLab cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Connecting Virtual Lab [Using Variable]

|  |  |
| --- | --- |
| This example shows how to connect the Exchange VLab 01 virtual lab to Veeam Backup & Replication.  |  | | --- | | $server = Get-VBRServer -Name "ESXiHost"  $VLab01 = Find-VSBVirtualLab -Server $server -Name "Exchange VLab 01"  Connect-VSBVirtualLab -VirtualLab $VLab01 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VSBVirtualLab](find-vsbvirtuallab.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $VLab01 variable. 3. Run the Connect-VSBVirtualLab cmdlet. Set the $VLab01 variable as the VirtualLab parameter value. |

Related Commands

[Find-VSBVirtualLab](find-vsbvirtuallab.md)


