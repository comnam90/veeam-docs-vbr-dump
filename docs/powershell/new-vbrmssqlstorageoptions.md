---
title: "New-VBRMSSQLStorageOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmssqlstorageoptions.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# New-VBRMSSQLStorageOptions


Short Description

Creates Microsoft SQL Server storage options configuration that defines compression, encryption, and full‑backup maintenance policies for SQL Server backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMSSQLStorageOptions [-EnableCompression] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>] [-EnableFullBackupMaintenance] [-FullBackupMaintenanceDays <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Microsoft SQL Server.

Use this cmdlet to create Microsoft SQL Server storage options. You can enable compression, encryption and full backup maintenance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableCompression | Enables compression of Microsoft SQL Server backup data. | SwitchParameter | False | Named | False |
| EnableEncryption | Enables encryption of the Microsoft SQL Server backup files. Requires an encryption key or KMS server definition. | SwitchParameter | False | Named | False |
| EncryptionKey | Specifies a local encryption key. Used when encryption is enabled. | Accepts the VBREncryptionKey object. To define this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies an external Key Management Server (KMS) configured in Veeam Backup & Replication. | Accepts the VBRKMSServer object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| EnableFullBackupMaintenance | Enables automatic maintenance of older full Microsoft SQL Server backups based on retention. | SwitchParameter | False | Named | False |
| FullBackupMaintenanceDays | Defines the number of days to retain full backup files before maintenance cleanup removes them.  Permitted values: 7 to 999. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Example 1. Enable Compression and Encryption for Microsoft SQL Server Application Backup Policy

This example shows how to configure compression and encryption for a Microsoft SQL Server application backup policy.

|  |
| --- |
| $key = Get‑VBREncryptionKey  New‑VBRMSSQLStorageOptions -EnableCompression -EnableEncryption -EncryptionKey $key |

Perform the following steps:

1. Run the [Get‑VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Save the result to the $key variable.
2. Run the New‑VBRMSSQLStorageOptions cmdlet. Provide the EnableCompression and EnableEncryption parameters. Specify the EncryptionKey parameter with the $key variable.

Example 2. Enable Full Backup Maintenance Policy for Application Backup Policy for Microsoft SQL Server

This example shows how to enable full backup maintenance for Microsoft SQL Server backups and specify the retention period in days after which older full backup files are automatically deleted.

|  |
| --- |
| New‑VBRMSSQLStorageOptions -EnableFullBackupMaintenance -FullBackupMaintenanceDays 30 |


