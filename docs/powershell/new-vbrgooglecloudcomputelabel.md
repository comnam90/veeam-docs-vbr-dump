---
title: "New-VBRGoogleCloudComputeLabel"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrgooglecloudcomputelabel.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRGoogleCloudComputeLabel

In this article

Short Description

Creates Google Cloud labels.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRGoogleCloudComputeLabel -Key <string> [-Value <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Google Cloud labels. You can use these labels to categorize instances in Google Cloud.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Key | Specifies a Google Cloud label key. The cmdlet will create a label with this key. | String | True | Named | False |
| Value | Specifies a key value for the Google Cloud label. The cmdlet will create the label with the specified key value. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeLabel](vbrgooglecloudcomputelabel.md)

Examples

Creating Google Cloud Label

This example shows how to create a new Google Cloud label with the location key and the west value of this key.

|  |
| --- |
| New-VBRGoogleCloudComputeLabel -Key "location" -Value "west" |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
