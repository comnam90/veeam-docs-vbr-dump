---
title: "New-VBROracleRMANStorageOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbroraclermanstorageoptions.html"
last_updated: "7/2/2025"
product_version: "13.0.1.1071"
---

# New-VBROracleRMANStorageOptions

In this article

Short Description

Creates the Oracle RMAN storage settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBROracleRMANStorageOptions [-CompressionEnabled] [-CompressionMode {Veeam | RMAN}] [-RMANCompressionLevel {Basic | Low | Medium | High}] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Oracle RMAN.

This cmdlet creates Oracle RMAN storage settings. You can set up the following options:

* Data compression mode.
* Data compression level.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CompressionEnabled | Enables the option for the application backup policy to apply compression to backups. | SwitchParameter | False | Named | False |
| CompressionMode | Specifies the compression level of backups:   * Veeam: use this option if you want to perform default data compression with Data Mover by Veeam Software. * RMAN: use this option if you want to perform data compression with Oracle RMAN. | VBRApplicationStorageCompressionMode | False | Named | False |
| RMANCompressionLevel | This parameter applies only with CompressionMode specified as RMAN.  Specifies the compression level of backups:   * Basic: use this option to set a basic compression level. * Low: use this option to set a low compression level. * Medium: use this option to set a medium compression level. * High: use this option to set a high compression level. | VBRRMANCompressionLevel | False | Named | False |
| EnableEncryption | Enables encryption for a specific application backup policy. Veeam Backup & Replication will encrypt the data that is passed between backup infrastructure components on the source and target side. | SwitchParameter | False | Named | False |
| EncryptionKey | Creates an encryption key for the specified application backup policy. | Accepts the VBREncryptionKey object. To define this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the VBRKMSServer object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBROracleRMANStorageOptions object that defines Oracle RMAN storage settings.

Examples

Creating Oracle RMAN Storage Settings for Application Backup Policies for Veeam Plug-In for Oracle RMAN

This command creates an Oracle RMAN storage settings for application backup policies for Veeam Plug-In for Oracle RMAN. The policy will apply low compression to backups using Oracle tools.

|  |
| --- |
| New-VBROracleRMANStorageOptions -CompressionEnabled -CompressionMode RMAN -RMANCompressionLevel Low |

Page updated 7/2/2025

Page content applies to build 13.0.1.1071
