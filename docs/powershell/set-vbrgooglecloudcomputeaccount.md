---
title: "Set-VBRGoogleCloudComputeAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgooglecloudcomputeaccount.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRGoogleCloudComputeAccount


Short Description

Modifies Google Cloud service account credentials record.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGoogleCloudComputeAccount -Account <VBRGoogleCloudComputeAccount> [-Name <string>] [-JSONKey <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing Google Cloud service account credentials record.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Google Cloud service account credentials record that you want to modify. | Accepts the VBRGoogleCloudComputeAccount object. To create this object, run the [Add-VBRGoogleCloudComputeAccount](add-vbrgooglecloudcomputeaccount.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the Google Cloud service account. Veeam Backup & Replication will modify the name of the Google Cloud service account to the specified value. | String | False | Named | False |
| JSONKey | Specifies the path to the service account key in the JSON format. Veeam Backup & Replication will modify the path to the Google Cloud service account key to the specified value. | String | False | Named | False |
| Description | Specifies a description for Google Cloud service account credentials records.  Veeam Backup & Replication will modify the description of the Google Cloud service account to the specified value. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeAccount](vbrgooglecloudcomputeaccount.md)

Examples

Modifying Google Cloud Service Account Credentials Record

This example shows how to modify the GCP service acc 1 Google Cloud service account credentials record.

|  |
| --- |
| $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service acc 1"  Set-VBRGoogleCloudComputeAccount -Account $account -Name "GCP service account 1" |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Set-VBRGoogleCloudComputeAccount cmdlet. Set the $account variable as the Account parameter. Specify the Name parameter value.

Related Commands

[Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md)


