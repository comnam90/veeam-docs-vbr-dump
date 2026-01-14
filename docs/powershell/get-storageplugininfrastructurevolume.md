---
title: "Get-StoragePluginInfrastructureVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-storageplugininfrastructurevolume.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-StoragePluginInfrastructureVolume

In this article

Short Description

Returns volumes of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-StoragePluginInfrastructureVolume [-Name <string[]>] [-Host <CPublicPluginHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of Universal Storage API integrated systems. The cmdlet will return storage volumes, even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-StoragePluginInfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies a storage. The cmdlet will return an array of volumes added to that storage. | Accepts the CVnxHost object. To get this object, run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

StoragePluginInfrastructureVolume

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Volumes Added to Universal Storage API Integrated Systems

|  |  |
| --- | --- |
| This command returns all volumes added to Universal Storage API integrated systems.  |  | | --- | | Get-StoragePluginInfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Volumes Added to Universal Storage API Integrated Systems by Name

|  |  |
| --- | --- |
| This command returns specific volumes added to Universal Storage API integrated systems.  |  | | --- | | Get-StoragePluginInfrastructureVolume -Name "Volume4", "Volume5", "Volume1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Volumes Added to Specific Universal Storage API Integrated System

|  |  |
| --- | --- |
| This example shows how to get all volumes added to the specific Universal Storage API integrated systems.  |  | | --- | | $storage = Get-StoragePluginHost -Name "IBM Spectrum"  Get-StoragePluginInfrastructureVolume -Name "VOLUME-01" -Host $storage |  Perform the following steps:   1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Get-StoragePluginInfrastructureVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value. |

Related Commands

[Get-StoragePluginHost](get-vnxhost.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
