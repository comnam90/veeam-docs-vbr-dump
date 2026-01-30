---
title: "Get-VBRGoogleCloudComputeZone"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputezone.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeZone


Short Description

Returns Google Cloud availability zones.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeZone -Region <VBRGoogleCloudComputeRegion> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Google Cloud availability zones.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Region | Specifies a Google Cloud region. The cmdlet will return availability zones for the specified Google Cloud region. | Accepts the VBRGoogleCloudComputeRegion object. To get this object, run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the availability zone. The cmdlet will return the availability zone with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeZone](vbrgooglecloudcomputezone.md)

Examples

Getting Availability Zones for Google Cloud Region

This example shows how to return availability zones for the Europe-west1 Google Cloud region.

|  |
| --- |
| $computeregion = Get-VBRGoogleCloudComputeRegion -Name "Europe-west1"  Get-VBRGoogleCloudComputeZone -Region $computeregion |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. Specify the Name parameter value. Save the result to the $computeregion variable.
2. Run the Get-VBRGoogleCloudComputeZone cmdlet. Set the $computeregion variable as the Region parameter.

Related Commands

[Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md)


