---
title: "Connect-VSBHvVirtualLab (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vsbhvvirtuallab.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Connect-VSBHvVirtualLab (obsolete)


Short Description

Connects an existing Hyper-V virtual lab.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works but may not be supported in further versions. |

Applies to

Platform: Hyper-V

For VMware, run the [Connect-VSBVirtualLab](connect-vsbvirtuallab.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VSBHvVirtualLab [-VirtualLab <CHvLabShortInfo>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet connects an existing Hyper-V virtual lab to Veeam Backup & Replication console.

When you add a new host to your Veeam Backup & Replication console, the virtual labs that are registered on it are not added automatically. Use this cmdlet to add the virtual labs to your Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies the virtual lab you want to connect to your Veeam Backup & Replication console. | Accepts the CHvLabShortInfo object. To get this object, run the [Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md) cmdlet. | True | 1 | True (ByValue,  ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Connecting Virtual Lab [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to connect the Exchange VLab 01 virtual lab.  |  | | --- | | $server = Get-VBRServer -Name "srv001"  Find-VSBHvVirtualLab -Server $server -Name "Exchange VLab 01" | Connect-VSBHvVirtualLab |  Perform the following steps:   1. Run the Get-VBRServer cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. 3. Pipe the cmdlet output to the Connect-VSBHvVirtualLab cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Connecting Virtual Lab [Using Variable]

|  |  |
| --- | --- |
| This example shows how to connect the Exchange VLab 01 virtual lab.  |  | | --- | | $server = Get-VBRServer -Name "srv001"  $VLab01 = Find-VSBHvVirtualLab -Server $server -Name "Exchange VLab 01"  Connect-VSBHvVirtualLab -VirtualLab $VLab01 |  Perform the following steps:   1. Run the Get-VBRServer cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $VLab01 variable. 3. Run the Connect-VSBHvVirtualLab cmdlet. Set the $VLab01 variable as the VirtualLab parameter value. |

Related Commands

[Find-VSBHvVirtualLab](find-vsbhvvirtuallab.md)


