---
title: "Get-ThinkSystemInfrastructureVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-thinksysteminfrastructurevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-ThinkSystemInfrastructureVolume

In this article

Short Description

Returns storage volumes of ThinkSystem storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-ThinkSystemInfrastructureVolume [-Name <string[]>] [-Host <CNaHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of ThinkSystem storage systems. The cmdlet will return storage volumes, even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-ThinkSystemInfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String | False | Named | False |
| Host | Specifies a storage system. The cmdlet will return volumes of this storage system. | Accepts the CNaHost object. To create this object, run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Storage Volumes

|  |  |
| --- | --- |
| This command returns volumes of all ThinkSystem storage systems.  |  | | --- | | Get-ThinkSystemInfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Storage Volumes by Name

|  |  |
| --- | --- |
| This command returns ThinkSystem storage volumes by the volume name.  |  | | --- | | Get-ThinkSystemInfrastructureVolume -Name "ISCSI Volume4", "ISCSI Volume5", "NFS Volume1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Volumes of Specific Storage System

|  |  |
| --- | --- |
| This example shows how to get all volumes of the specified ThinkSystem storage system.  |  | | --- | | $storage = Get-ThinkSystemHost -Name "ThinkSystem Store"  Get-VInfrastructureVolume -Host $storage |  Perform the following steps:   1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Get-ThinkSystemInfrastructureVolume cmdlet. Set the $storage variable as the Host parameter value. |

Related Commands

[Get-ThinkSystemHost](get-thinksystemhost.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
