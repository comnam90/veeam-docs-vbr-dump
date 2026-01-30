---
title: "Get-VBREncryptedBackupHint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrencryptedbackuphint.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Get-VBREncryptedBackupHint


Short Description

Returns password hints for imported encrypted backups.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREncryptedBackupHint -Backup <VBRImportedEncryptedBackup>  [<CommonParameters>] |

Detailed Description

This cmdlet returns password hints for a selected imported encrypted backup.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the imported encrypted backup. The cmdlet will return hints for this backup. | Accepts the [VBRImportedEncryptedBackup](vbrimportedencryptedbackup.md) object. To get this object, run the [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRImportedEncryptedBackupHint](vbrimportedencryptedbackuphint.md)

Examples

Getting Password Hints for Imported Encrypted Backup

This example shows how to get the password hints for an imported encrypted backup.

|  |
| --- |
| $encryptedbackup = Get-VBRImportedEncryptedBackup -Name "Atlanta SQL Server Backup"  Get-VBREncryptedBackupHint -Backup $encryptedbackup |

Perform the following steps:

1. Run the [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $encryptedbackup variable.
2. Run the Get-VBREncryptedBackupHint cmdlet. Set the $encryptedbackup variable as the Backup parameter value.

Related Commands

[Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md)


