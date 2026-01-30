---
title: "Get-HP3InfrastructureVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-hp3infrastructurevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-HP3InfrastructureVolume


Short Description

Returns volumes of HPE 3PAR StoreServ storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-HP3InfrastructureVolume [-Name <string[]>] [-Storage <CHp3PARHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of HPE 3PAR StoreServ storage systems. The cmdlet will return storage volumes, even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-HP3InfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Storage | Specifies a storage system. The cmdlet will return an array of the volumes added to that storage system. | Accepts the CHp3PARHost object. To get this object, run the [Get-HP3Storage](get-hp3storage.md) cmdlet. | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

HP3InfrastructureVolume

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Volumes Added to HPE 3PAR StoreServ Storage Systems

|  |  |
| --- | --- |
| This command returns all volumes added to HPE 3PAR StoreServ storage systems.  |  | | --- | | Get-HP3InfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific HPE 3PAR StoreServ Storage Volumes

|  |  |
| --- | --- |
| This command returns specific HPE 3PAR StoreServ storage volumes. Use the Name parameter to specify the names of the volumes.  |  | | --- | | Get-HP3InfrastructureVolume -Name "ISCSI Volume4", "ISCSI Volume5", "NFS Volume1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Volumes Added to Specific HPE 3PAR StoreServ Storage System

|  |  |
| --- | --- |
| This example shows how to get all volumes added to the specific HPE 3PAR StoreServ storage system.  |  | | --- | | $storage = Get-HP3Storage -Name "HPE 3PAR StoreServe Storage"  Get-HP3InfrastructureVolume -Storage $storage |  Perform the following steps:   1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Get-HP3InfrastructureVolume cmdlet. Set the $storage variable as the Storage parameter value. |

Related Commands

[Get-HP3Storage](get-hp3storage.md)


