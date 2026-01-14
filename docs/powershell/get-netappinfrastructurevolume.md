---
title: "Get-NetAppInfrastructureVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-netappinfrastructurevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-NetAppInfrastructureVolume

In this article

Short Description

Returns storage volumes of NetApp storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NetAppInfrastructureVolume [-Name <string[]>] [-Host <CNaHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of NetApp storage systems. The cmdlet will return storage volumes, even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-NetAppInfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies a storage system. The cmdlet will return volumes of this storage system. | Accepts the CNaHost object. To get this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

NetAppInfrastructureVolume

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Volumes of All NetApp Storage Systems

|  |  |
| --- | --- |
| This command returns volumes of all NetApp storage systems.  |  | | --- | | Get-NetAppInfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting NetApp Storage Volumes by Name

|  |  |
| --- | --- |
| This command returns NetApp storage volumes by the volume name.  |  | | --- | | Get-NetAppInfrastructureVolume -Name "ISCSI Volume4", "ISCSI Volume5", "NFS Volume1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Volumes of Specific NetApp Storage System

|  |  |
| --- | --- |
| This example shows how to get all volumes of the specified NetApp storage system.  |  | | --- | | $storage = Get-NetAppHost -Name "NetApp Store"  Get-NetAppInfrastructureVolume -Host $storage |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the Get-NetAppInfrastructureVolume cmdlet. Set the $storage variable as the Host parameter value. |

Related Commands

[Get-NetAppHost](get-netapphost.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
