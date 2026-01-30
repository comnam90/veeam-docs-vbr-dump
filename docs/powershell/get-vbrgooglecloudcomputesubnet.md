---
title: "Get-VBRGoogleCloudComputeSubnet"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputesubnet.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeSubnet


Short Description

Returns subnets for Google Cloud region.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeSubnet -Region <VBRGoogleCloudComputeRegion> [-VPC <VBRGoogleCloudComputeVPC>] [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns subnets for Google Cloud region.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Region | Specifies a Google Cloud region. The cmdlet will return subnets for the specified Google Cloud region. | Accepts the VBRGoogleCloudComputeRegion object. To get this object, run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. | True | Named | False |
| VPC | Specifies a Google Cloud VPC network. The cmdlet will return subnets for the specified Google Cloud VPC network. | Accepts the VBRGoogleCloudComputeVPC object. To get this object, run the [Get-VBRGoogleCloudComputeVPC](get-vbrgooglecloudcomputevpc.md) cmdlet. | False | Named | False |
| Name | Specifies a name of the subnet. The cmdlet will return the subnet with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeSubnet](vbrgooglecloudcomputesubnet.md)

Examples

Getting Subnets for Google Cloud Region

This example shows how to get subnets for the Europe-west1 Google Cloud region and VPC network of the GCP service account 1 Google Cloud service account.

|  |
| --- |
| $computeregion = Get-VBRGoogleCloudComputeRegion -Name "Europe-west1"  $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service account 1"  $vpc = Get-VBRGoogleCloudComputeVPC -Account $account  Get-VBRGoogleCloudComputeSubnet -Region $computeregion -VPC $vpc |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. Specify the Name parameter value. Save the result to the $computeregion variable.
2. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
3. Run the [Get-VBRGoogleCloudComputeVPC](get-vbrgooglecloudcomputevpc.md) cmdlet. Set the $account variable as the Account parameter. Save the result to the $vpc variable.
4. Run the Get-VBRGoogleCloudComputeSubnet cmdlet. Set the $computeregion variable as the Region parameter. Set the $vpc variable as the VPC parameter.

Related Commands

* [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md)
* [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md)
* [Get-VBRGoogleCloudComputeVPC](get-vbrgooglecloudcomputevpc.md)


