---
title: "Add-VSBHvVirtualLab (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbhvvirtuallab.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Add-VSBHvVirtualLab (obsolete)

In this article

Short Description

Creates a Hyper-V virtual lab.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. Run the [Add-VBRApplicationGroup](add-vbrapplicationgroup.md) cmdlet instead. |

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VSBHvVirtualLab -Name <String> -Server <CHost> -Folder <String> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Hyper-V virtual lab.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the virtual lab. | String | True | Named | False |
| Server | Specifies the Hyper-V host where the virtual lab should be created. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Folder | Specifies the path to the folder where the redo log files of the virtual lab will be stored. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Hyper-V Virtual Lab

This example shows how to create the Exchange VLab 01 Hyper-V virtual lab.

|  |
| --- |
| $server = Get-VBRServer -Name "esx05.tech.local"  Add-VSBHvVirtualLab -Name "Exchange VLab 01" -Server $server -Folder "c:\VirtualLabs" |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter. Save the result to the $server variable.
2. Run the Add-VSBHvVirtualLab cmdlet. Specify the Name parameter. Set the $server variable as the Server parameter value. Specify the Path parameter.

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
