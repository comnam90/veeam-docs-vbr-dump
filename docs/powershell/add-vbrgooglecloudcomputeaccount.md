---
title: "Add-VBRGoogleCloudComputeAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrgooglecloudcomputeaccount.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRGoogleCloudComputeAccount

In this article

Short Description

Adds Google Cloud service account credentials record.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRGoogleCloudComputeAccount -Name <string> -JSONKey <string> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds the [VBRGoogleCloudComputeAccount](vbrgooglecloudcomputeaccount.md) object. This object contains Google Cloud service account credentials records used to access the following services:

* Google Compute Engine.

* Google Cloud Plug-in for Veeam Backup & Replication.

|  |
| --- |
| Important |
| This cmdlet does not create a Google Cloud service account. You must set up the Google Cloud service account beforehand, as described in [Google Cloud documentation](https://cloud.google.com/iam/docs/creating-managing-service-account-keys). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of the Google Cloud service account. Veeam Backup & Replication will save the Google Cloud service account under this name. | String | True | Named | False |
| JSONKey | Specifies the path to the service account key in the JSON format. | String | True | Named | False |
| Description | Specifies a description for Google Cloud service account credentials records. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeAccount](vbrgooglecloudcomputeaccount.md)

Examples

Creating Google Cloud Service Account

This command creates the GCP service acc 1 Google Cloud service account credentials record. The cmdlet will use the json key located at the C:\Users\Admin\Downloads\eu-backup-253812-1bd00366edd2.json path.

|  |
| --- |
| Add-VBRGoogleCloudComputeAccount -Name "GCP service acc 1" -JSONKey "C:\Users\Admin\Downloads\eu-backup-253812-1bd00366edd2.json" -Description "Google Cloud Compute Administrator 1" |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
