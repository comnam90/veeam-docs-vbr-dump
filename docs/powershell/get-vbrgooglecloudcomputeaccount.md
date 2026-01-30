---
title: "Get-VBRGoogleCloudComputeAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudcomputeaccount.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudComputeAccount


Short Description

Returns Google Cloud service account credentials record.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudComputeAccount [-Id <guid>] [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Google Cloud service account credential records.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an ID of the service account. The cmdlet will return the service account with this ID. | Guid | False | Named | False |
| Name | Specifies a name of the service account. The cmdlet will return the service account with this name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeAccount](vbrgooglecloudcomputeaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. ![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Getting Google Cloud Service Account by ID

|  |  |
| --- | --- |
| This command gets a Google Cloud service account credentials record with the 860aa7c0-3f4d-44f8-9deb-f86196f37660 ID.  |  | | --- | | Get-VBRGoogleCloudComputeAccount -Id "860aa7c0-3f4d-44f8-9deb-f86196f37660" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. ![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Getting Google Cloud Service Account by Name

|  |  |
| --- | --- |
| This command gets a Google Cloud credentials record with the GCP service acc 1 name.  |  | | --- | | Get-VBRGoogleCloudComputeAccount -Name "GCP service acc 1" | |


