---
title: "Get-VBRGoogleCloudAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudaccount.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudAccount


Short Description

Returns Google Cloud credentials records.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Google Cloud credentials records by the access key.

|  |
| --- |
| Get-VBRGoogleCloudAccount [-AccessKey <string[]>]  [<CommonParameters>] |

* Get Google Cloud credentials records by the ID.

|  |
| --- |
| Get-VBRGoogleCloudAccount -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of existing Google Cloud credentials records managed by Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for Google Cloud credentials records. The cmdlet will return Google Cloud credentials records with these IDs. | Guid[] | True | Named | True (ByValue, ByPropertyName) |
| AccessKey | Specifies an array of access keys for Google Cloud credentials records. The cmdlet will return Google Cloud credentials records with these access keys. | String[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudAccount object that contains the credentials records to access the Google Cloud service.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Google Cloud Account by Access Key

|  |  |
| --- | --- |
| This command gets a Google Cloud credentials record by the access key.  |  | | --- | | Get-VBRGoogleCloudAccount -AccessKey "XXXXXXXXXXXXXXXXXXXXXXX" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Google Cloud Account by ID

|  |  |
| --- | --- |
| This command gets a Google Cloud credentials record by the ID.  |  | | --- | | Get-VBRGoogleCloudAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c", "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c" | |


