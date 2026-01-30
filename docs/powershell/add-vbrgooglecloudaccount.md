---
title: "Add-VBRGoogleCloudAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrgooglecloudaccount.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Add-VBRGoogleCloudAccount


Short Description

Creates Google Cloud credentials records.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRGoogleCloudAccount -AccessKey <string> -SecretKey <string> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the credentials records to access the Google Cloud service.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| AccessKey | Specifies an access key. The cmdlet will use this key to add Google Cloud credentials records to Veeam Backup & Replication. | String | True | Named | False |
| SecretKey | Specifies a secret key. The cmdlet will use this secret key to add the Google Cloud credentials records to Veeam Backup & Replication. | String | True | Named | False |
| Description | Specifies a description for Google Cloud credentials records. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudAccount object that contains the credentials records to access the Google Cloud service.

Examples

Creating Google Cloud Account

This command creates a Google Cloud credentials record.

|  |
| --- |
| Add-VBRGoogleCloudAccount -AccessKey "XXXXXXXXXXXXX" -SecretKey "XXXXXXXXXXXX" -Description "Google Cloud Administrator" |


