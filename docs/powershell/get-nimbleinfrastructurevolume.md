---
title: "Get-NimbleInfrastructureVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-nimbleinfrastructurevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-NimbleInfrastructureVolume


Short Description

Returns volumes of HPE Nimble storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NimbleInfrastructureVolume [-Name <string[]>] [-Host <CNimbleHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of HPE Nimble storage systems. The cmdlet will return storage volumes, even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-NimbleInfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies a storage. The cmdlet will return an array of volumes added to that storage system. | Accepts the CNimbleHost object. To get this object, run the [Get-NimbleHost](get-nimblehost.md) cmdlet. | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

NimbleInfrastructureVolume

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Volumes of HPE Nimble Storage System

|  |  |
| --- | --- |
| This command returns all volumes added to an HPE Nimble storage system.  |  | | --- | | Get-NimbleInfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific HPE Nimble Volumes

|  |  |
| --- | --- |
| This command returns specific HPE Nimble volumes.  |  | | --- | | Get-NimbleInfrastructureVolume -Name "Volume4", "Volume5", "Volume1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Volumes Added to Specific HPE Nimble Storage System

|  |  |
| --- | --- |
| This example shows how to get all volumes added to the specific HPE Nimble storage system.  |  | | --- | | $storage = Get-NimbleHost -Name "HPE Nimble-FC"  Get-NimbleInfrastructureVolume -Host $storage |  Perform the following steps:   1. Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Get-NimbleInfrastructureVolume cmdlet. Set the $storage variable as the Host parameter value. |

Related Commands

[Get-NimbleHost](get-nimblehost.md)


