---
title: "Get-VBRNutanixInfrastructureVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnutanixinfrastructurevolume.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNutanixInfrastructureVolume

In this article

Short Description

Returns Nutanix Files volumes added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNutanixInfrastructureVolume [-Name <string[]>] [-Host <CNutanixHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of Nutanix Files storage systems. The cmdlet will return storage volumes even if they are not added to your backup infrastructure.

|  |
| --- |
| Tip |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies a storage system. The cmdlet will return an array of volumes added to that storage system. | Accepts the CNutanixHost object. To create this object, run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CSanInfrastructureVolume[] objects that define volume settings.

Examples

Getting Volumes of Nutanix Files Storage Systems

This example shows how to get an array of volumes of Nutanix Files storage systems.

|  |
| --- |
| $host = Get-VBRNutanixHost -Name "Nutanix Files\_host"  Get-VBRNutanixInfrastructureVolume -Host $host |

Perform the following steps:

1. Run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable.
2. Run the Get-VBRNutanixInfrastructureVolume cmdlet. Set the $host variable as the Host parameter value.

Related Commands

[Get-VBRNutanixHost](get-vbrnutanixhost.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
