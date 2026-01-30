---
title: "Remove-VBRGoogleCloudComputeAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrgooglecloudcomputeaccount.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRGoogleCloudComputeAccount


Short Description

Removes Google Cloud service account credentials records.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRGoogleCloudComputeAccount -Account <VBRGoogleCloudComputeAccount>  [<CommonParameters>] |

Detailed Description

This cmdlet removes Google Cloud service account credentials records.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Google Cloud service account credentials record that you want to remove. | Accepts the VBRGoogleCloudComputeAccount object. To create this object, run the [Add-VBRGoogleCloudComputeAccount](add-vbrgooglecloudcomputeaccount.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeAccount](vbrgooglecloudcomputeaccount.md)

Examples

Removing Google Cloud Service Account Credentials Record

This example shows how to remove the GCP service account 1 Google Cloud service account credentials record.

|  |
| --- |
| $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service account 1"  Remove-VBRGoogleCloudComputeAccount -Account $account |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Remove-VBRGoogleCloudComputeAccount cmdlet. Set the $account variable as the Account parameter.

Related Commands

[Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)


