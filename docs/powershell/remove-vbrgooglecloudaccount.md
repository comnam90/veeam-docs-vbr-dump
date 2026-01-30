---
title: "Remove-VBRGoogleCloudAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrgooglecloudaccount.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRGoogleCloudAccount


Short Description

Removes Google Cloud credentials records from Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRGoogleCloudAccount -Account <VBRGoogleCloudAccount> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Google Cloud credentials records from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies Google Cloud credentials records that you want to remove. | Accepts the VBRGoogleCloudAccount object. To create this object, run the [Add-VBRGoogleCloudAccount](add-vbrgooglecloudaccount.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Google Cloud Credentials Record

This example shows how to remove a Google Cloud credentials record.

|  |
| --- |
| $creds = Get-VBRGoogleCloudAccount -AccessKey "ABCDEFGHIGKLMNOP"  Remove-VBRGoogleCloudAccount -Account $creds |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $creds variable.
2. Run the Remove-VBRGoogleCloudAccount cmdlet. Set the $creds variable as the Account parameter value.

Related Commands

[Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)


