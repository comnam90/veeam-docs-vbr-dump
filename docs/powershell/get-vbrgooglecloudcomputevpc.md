---
title: "Get-VBRGoogleCloudComputeVPC"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputevpc.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeVPC

In this article

Short Description

Returns Virtual Private Cloud (VPC) networks.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeVPC -Account <VBRGoogleCloudComputeAccount> -Name <string>  [<CommonParameters>] |

Detailed Description

This cmdlet returns VPC networks.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Google Cloud service account. The cmdlet will return VPC networks for the specified Google Cloud service account. | Accepts the VBRGoogleCloudComputeAccount object. To create this object, run the [Add-VBRGoogleCloudComputeAccount](add-vbrgooglecloudcomputeaccount.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the VPC network. The cmdlet will return the VPC network with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeVPC](vbrgooglecloudcomputevpc.md)

Examples

Getting VPC Networks for Google Cloud Service Account

This example shows how to get VPC networks for the GCP service account 1 Google Cloud service account.

|  |
| --- |
| $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service account 1"  Get-VBRGoogleCloudComputeVPC -Account $account |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Get-VBRGoogleCloudComputeVPC cmdlet. Set the $account variable as the Account parameter.

Related Commands

[Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
