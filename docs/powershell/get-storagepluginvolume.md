---
title: "Get-StoragePluginVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-storagepluginvolume.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-StoragePluginVolume


Short Description

Returns volumes of Universal Storage API integrated systems added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Get-StoragePluginVolume [-Name <String[]>] [-Host <CPublicPluginHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns volumes of Universal Storage API integrated systems added to the backup infrastructure.

|  |
| --- |
| Tip |
| Run the [Get-StoragePluginInfrastructureVolume](get-storageplugininfrastructurevolume.md) cmdlet to get an array of volumes from Universal Storage API integrated systems. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies an array of storage systems. The cmdlet will return volumes of these storage systems. | Accepts the CPublicPluginHost[] object. To get this object, run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting Universal API Integrated System Volume

This example shows how to get a Universal Storage API integrated systems volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-StoragePluginHost -Name "IBM Spectrum"  Get-StoragePluginVolume -Name "VOLUME-01" -Host $storage |

Perform the following steps:

1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-StoragePluginVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value.

Related Commands

[Get-StoragePluginHost](get-storagepluginhost.md)


