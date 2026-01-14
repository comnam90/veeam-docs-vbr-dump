---
title: "Get-VBRNutanixHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnutanixhost.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNutanixHost

In this article

Short Description

Returns Nutanix Files storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNutanixHost [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Nutanix Files storage systems. You can get the list of all Nutanix Files storage systems added to your virtual infrastructure or narrow down the output by a storage system name.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of storage system names. The cmdlet will return storage systems with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CNutanixHost object that defines the settings of a Nutanix Files storage system.

Examples

Getting Nutanix Files Storage Systems

This command gets Nutanix Files storage systems.

|  |
| --- |
| Get-VBRNutanixHost -Name "Nutanix Files\_host" |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
