---
title: "Get-VNXInfrastructureVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vnxinfrastructurevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-VNXInfrastructureVolume


Short Description

Returns volumes of Dell VNX storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VNXInfrastructureVolume [-Name <string[]>] [-Host <CVnxHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of Dell VNX storage systems. The cmdlet will return storage volumes, even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-VNXInfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies a storage. The cmdlet will return an array of volumes added to that storage system. | Accepts the CVnxHost object. To get this object, run the [Get-VNXHost](get-vnxhost.md) cmdlet. | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VNXInfrastructureVolume

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Volumes Added to Dell VNX Storage Systems

|  |  |
| --- | --- |
| This command returns all volumes added to Dell VNX storage systems.  |  | | --- | | Get-VNXInfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Dell VNX Storage Volumes by Name

|  |  |
| --- | --- |
| This command returns Dell VNX storage volumes by the volume name.  |  | | --- | | Get-VNXInfrastructureVolume -Name "Volume4", "Volume5", "Volume1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Volumes Added to Specific Dell VNX Storage

|  |  |
| --- | --- |
| This example shows how to all volumes added to the specific Dell VNX storage.  |  | | --- | | $storage = Get-VNXHost -Name "VNX Storage"  Get-VNXInfrastructureVolume -Host $storage |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Get-VNXInfrastructureVolume cmdlet. Set the $storage variable as the Host parameter value. |

Related Commands

[Get-VNXHost](get-vnxhost.md)


