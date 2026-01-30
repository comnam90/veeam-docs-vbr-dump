---
title: "Get-VBRNutanixVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnutanixvolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNutanixVolume


Short Description

Returns all volumes of the specified Nutanix Files storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNutanixVolume [-Name <string[]>] [-Host <CNutanixHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Nutanix Files volumes added to the backup infrastructure.

|  |
| --- |
| Tip |
| Run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet to get an array of all volumes of Nutanix Files storage systems. The cmdlet will also return volumes not added to the backup infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Host | Specifies a storage system. The cmdlet will return an array of volumes added to that storage system. | Accepts the CNutanixHost object. To create this object, run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CSanVolume object that defines volume settings.

Examples

Getting Nutanix Files Volumes

This command gets Nutanix Files volumes.

|  |
| --- |
| Get-VBRNutanixVolume -Name "VOL01" |


