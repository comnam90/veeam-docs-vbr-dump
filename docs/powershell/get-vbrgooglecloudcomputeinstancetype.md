---
title: "Get-VBRGoogleCloudComputeInstanceType"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputeinstancetype.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeInstanceType

In this article

Short Description

Returns Google Cloud VM instance types.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeInstanceType -Zone <VBRGoogleCloudComputeZone> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Google Cloud VM instance types and information about the memory and the CPU available for each VM instance type.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Zone | Specifies a Google Cloud availability zone. The cmdlet will return an array of Google Cloud VM instance types that are available for the specified availability zone. | Accepts the VBRGoogleCloudComputeZone object. To get this object, run the [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md) cmdlet. | True | Named | False |
| Name | Specifies the name of the Google Cloud VM instance type. The cmdlet will return the VM instance type with this name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeInstanceType](vbrgooglecloudcomputeinstancetype.md)

Examples

Getting VM Instance Types for Google Cloud Region

This example shows how to get an array of VM instance types for the Europe-west1 Google Cloud region.

|  |
| --- |
| $computeregion = Get-VBRGoogleCloudComputeRegion -Name "Europe-west1"  $computezone = Get-VBRGoogleCloudComputeZone -Region $computeregion  Get-VBRGoogleCloudComputeInstanceType -Zone $computezone |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. Specify the Name parameter value. Save the result to the $computeregion variable.
2. Run the [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md) cmdlet. Set the $computeregion variable as the Region parameter. Save the result to the $computezone parameter value.
3. Run the Get-VBRGoogleCloudComputeInstanceType cmdlet. Set the $computezone variable as the Zone parameter.

Related Commands

* [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md)
* [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
