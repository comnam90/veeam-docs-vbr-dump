---
title: "Find-VSBHvVirtualLab (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vsbhvvirtuallab.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Find-VSBHvVirtualLab (obsolete)

In this article

Short Description

Looks for virtual labs created on the specified Hyper-V host.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Find-VSBVirtualLab -Server <CHost> [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns virtual labs created on the specified Hyper-V host, both registered in Veeam Backup & Replication and not.

You can get the list of all virtual labs on the specified Hyper-V host or look for instances directly by name.

Run the [Connect-VSBHvVirtualLab](connect-vsbhvvirtuallab.md) cmdlet to add the unregistered virtual labs to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Hyper-V host. The cmdlet will return virtual labs created on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the array of names of the virtual labs. The cmdlet will return virtual labs with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CHvSbVirtualLab

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Labs on Specific Hyper-V Server [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get all virtual labs created on the Hyper-V Host Hyper-V server.  |  | | --- | | Get-VBRServer -Name "Hyper-V Host" | Find-VSBHvVirtualLab |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Find-VSBHvVirtualLab cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Labs on Specific Hyper-V Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get virtual labs with names starting with "Hv" on the Hyper-V Host Hyper-V server.  |  | | --- | | $server = Get-VBRServer -Name "Hyper-V Host"  Find-VSBHvVirtualLab -Server $server -Name Hv\* |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VSBHvVirtualLab cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
