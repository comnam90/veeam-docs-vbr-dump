---
title: "Get-VBRGoogleCloudComputeSharedSubnet"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputesharedsubnet.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeSharedSubnet

In this article

Short Description

Returns subnets of Google Cloud shared VPC network.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeSharedSubnet -Account <VBRGoogleCloudComputeAccount> [-Region <string>] [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns subnets of Google Cloud shared VPC network.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Google Cloud service account. The cmdlet will return subnets of the shared VPC network for the specified Google Cloud service account. | Accepts the VBRGoogleCloudComputeAccount object. To create this object, run the [Add-VBRGoogleCloudComputeAccount](add-vbrgooglecloudcomputeaccount.md) cmdlet. | True | Named | False |
| Region | Specifies a Google Cloud region. The cmdlet will return subnets of the shared VPC for the specified Google Cloud region. | Accepts the VBRGoogleCloudComputeRegion object. To get this object, run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. | False | Named | False |
| Name | Specifies a name of the subnet. The cmdlet will return the subnet with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeSubnet](vbrgooglecloudcomputesubnet.md)

Examples

Getting Subnets of Shared VPC Network for Google Cloud Service Account

This example shows how to get subnets of the shared VPC network for the GCP service acc 1 Google Cloud service account.

|  |
| --- |
| $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service acc 1"  Get-VBRGoogleCloudComputeSharedSubnet -Account $account |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Get-VBRGoogleCloudComputeSharedSubnet cmdlet. Set the $account variable as the Account parameter.

Related Commands

[Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
