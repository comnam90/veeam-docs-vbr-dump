---
title: "Set-VBREncryptedBackupPassword"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrencryptedbackuppassword.html"
last_updated: "4/30/2025"
product_version: "13.0.1.1071"
---

# Set-VBREncryptedBackupPassword


Short Description

Decrypts imported encrypted backups.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Decrypt backups encrypted with a password.

|  |
| --- |
| Set-VBREncryptedBackupPassword -Backup <VBRImportedEncryptedBackup> -Password <String[]>  [<CommonParameters>] |

* Decrypt backups encrypted with the KMS Server.

|  |
| --- |
| Set-VBREncryptedBackupPassword -Backup <VBRImportedEncryptedBackup> -DecryptionSet <VBRDecryptionSet[]>  [<CommonParameters>] |

Detailed Description

This cmdlet decrypts a selected imported encrypted backup. After you decrypt an imported encrypted backup, you can use such backups for restore. The decrypted backups will be available in the array of backups returned by the [Get-VBRBackup](get-vbrbackup.md) cmdlet.

To decrypt an imported encrypted backup, you will need to specify the password or passwords you used to encrypt the backups. If you changed the password one or several times while the backup chain was created, you must enter passwords in the following manner:

* If you decrypt a VBM file, you must specify the latest password that was used to encrypt files in the backup chain.
* If you decrypt a VBK file, you must specify the whole set of passwords that were used to encrypt files in the backup chain.
* [For a new Veeam Backup & Replication installation] When you run separate catalog jobs for tapes encrypted with the KMS solution and tapes encrypted with password-based keys.

You can use hints to recall the passwords you used to encrypt the backups. Run the [Get-VBRImportedEncryptedBackupHint](get-vbrencryptedbackuphint.md) cmdlet to get the hints for the needed backup.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the imported encrypted backup you want to decrypt. | Accepts the [VBRImportedEncryptedBackup](vbrimportedencryptedbackup.md) object. To get this object, run the [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md) cmdlet. | True | Named | False |
| Password | Specifies the password required for decrypting the backup. | String[] | True | Named | False |
| DecryptionSet | Specifies the data decryption settings if the KMS Server was used for encryption. | Accepts the VBRDecryptionSet[] object. To get this object, run the [New-VBRDecryptionSet](new-vbrdecryptionset.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Decrypting Imported Encrypted Backup

This example shows how to decrypt an imported encrypted backup.

|  |
| --- |
| $encryptedbackup = Get-VBRImportedEncryptedBackup -Name "Atlanta SQL Server Backup"  Get-VBRImportedEncryptedBackupHint -Backup $encryptedbackup  Set-VBREncryptedBackupPassword -Backup $encryptedbackup -Password "123", "345" |

Perform the following steps:

1. Run the [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $encryptedbackup variable.
2. Run the [Get-VBRImportedEncryptedBackupHint](get-vbrencryptedbackuphint.md) cmdlet. Set the $encryptedbackup variable as the Backup parameter value.
3. Run the Set-VBREncryptedBackupPassword cmdlet. Set the $encryptedbackup variable as the Backup parameter value. Specify the Password parameter value.

Related Commands

* [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md)
* [Get-VBRImportedEncryptedBackupHint](get-vbrencryptedbackuphint.md)


