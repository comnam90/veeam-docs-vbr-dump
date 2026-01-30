---
title: "Get-VBRGoogleCloudComputeRegion"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputeregion.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeRegion


Short Description

Returns Google Cloud regions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeRegion -Account <VBRGoogleCloudComputeAccount> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Google Cloud regions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Google Cloud service account. The cmdlet will return regions for the specified Google Cloud service account. | Accepts the VBRGoogleCloudComputeAccount object. To create this object, run the [Add-VBRGoogleCloudComputeAccount](add-vbrgooglecloudcomputeaccount.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the Google Cloud region. The cmdlet will return the region with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeRegion](vbrgooglecloudcomputeregion.md)

Examples

Getting Regions for Google Cloud Service Account

This example shows how to return regions for the GCP service acc 1 Google Cloud service account.

|  |
| --- |
| $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service acc 1"  Get-VBRGoogleCloudComputeRegion -Account $account |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Get-VBRGoogleCloudComputeRegion cmdlet. Set the $account variable as the Account parameter.

Related Commands

[Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md)


