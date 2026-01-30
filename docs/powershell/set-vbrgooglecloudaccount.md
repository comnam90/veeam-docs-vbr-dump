---
title: "Set-VBRGoogleCloudAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgooglecloudaccount.html"
last_updated: "2/7/2024"
product_version: "13.0.1.1071"
---

# Set-VBRGoogleCloudAccount


Short Description

Modifies Google Cloud credentials records.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGoogleCloudAccount -Account <VBRGoogleCloudAccount> [-AccessKey <string>] [-SecretKey <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to modify Google Cloud credentials records.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies Google Cloud credentials records that you want to modify. | Accepts the VBRGoogleCloudAccount object. To create this object, run the [Add-VBRGoogleCloudAccount](add-vbrgooglecloudaccount.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description for  Google Cloud credentials records. | String | False | Named | False |
| AccessKey | Specifies an access key. The cmdlet will use this access key to add  Google Cloud credentials records to Veeam Backup & Replication. | String | False | Named | False |
| SecretKey | Specifies a secret key. The cmdlet will use this secret key to add Google Cloud credentials records to Veeam Backup & Replication. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudAccount object that contains the credentials records to access the Google Cloud service.

Examples

Setting up Google Cloud Account

This example shows how to modify a Google Cloud credentials record.

|  |
| --- |
| $creds = Get-VBRGoogleCloudAccount -AccessKey "ABCDEFGHIGKLMNOP"  Set-VBRGoogleCloudAccount -Account $creds -SecretKey "vmdkfdvdvdvEIE" |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $creds variable.
2. Run the Set-VBRGoogleCloudAccount cmdlet. Set the $creds variable as the Account parameter value. Specify the SecretKey parameter value.

Related Commands

[Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)


