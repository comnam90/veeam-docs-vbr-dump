---
title: "Get-VBREncryptedBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrencryptedbackup.html"
last_updated: "4/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBREncryptedBackup


Short Description

Returns encrypted backups.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREncryptedBackup [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns encrypted backups.

You can get the list of all encrypted backups or narrow down the output by the backups names.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of names of the imported encrypted backups. The cmdlet will return backups with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRImportedEncryptedBackup](vbrimportedencryptedbackup.md) object that defines encrypted backups.

Alias

Get-VBRImportedEncryptedBackup

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Returning all Encrypted Backups

|  |  |
| --- | --- |
| This command returns all encrypted backups.  |  | | --- | | Get-VBREncryptedBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Returning Specific Encrypted Backup

|  |  |
| --- | --- |
| This command returns an encrypted backup named Atlanta SQL Server Backup.  |  | | --- | | Get-VBREncryptedBackup -Name "Atlanta SQL Server Backup" | |


