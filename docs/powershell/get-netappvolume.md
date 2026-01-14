---
title: "Get-NetAppVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-netappvolume.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-NetAppVolume

In this article

Short Description

Returns NetApp storage volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NetAppVolume [-Name <String[]>] [-Host <CNaHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns NetApp storage volumes added to the backup infrastructure.

|  |
| --- |
| ![Get-NetAppVolume](images/icon_tip.webp) Tip: |
| Run the [Get-NetAppInfrastructureVolume](get-netappinfrastructurevolume.md) cmdlet to get an array of volumes from a NetApp storage system. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies an array of storage systems. The cmdlet will return volumes of these storage systems. | Accepts the CNaHost[] object. To get this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting Specific NetApp Storage Volume

This example shows how to get a specific NetApp storage volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-NetAppHost -Name "NetApp Store"  Get-NetAppVolume -Name "NetApp Volume 01" -Host $storage |

Perform the following steps:

1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-NetAppVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value.

Related Commands

[Get-NetAppHost](get-netapphost.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
