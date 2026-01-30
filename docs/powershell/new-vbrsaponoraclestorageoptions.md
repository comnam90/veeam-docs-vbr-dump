---
title: "New-VBRSAPOnOracleStorageOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsaponoraclestorageoptions.html"
last_updated: "7/2/2025"
product_version: "13.0.1.1071"
---

# New-VBRSAPOnOracleStorageOptions


Short Description

Creates the SAP on Oracle storage settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSAPOnOracleStorageOptions [-CompressionEnabled] [-CompressionMode <VBRApplicationStorageCompressionMode>] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for SAP on Oracle.

This cmdlet creates SAP on Oracle storage settings. You can set up the data compression mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CompressionEnabled | Defines that the application backup policy will apply compression to backups. | SwitchParameter | False | Named | False |
| CompressionMode | Specifies the compression level of backups:   * Veeam: use this option if you want to perform default data compression with Data Mover by Veeam Software. * RMAN: use this option if you want to perform data compression with Oracle RMAN. | VBRApplicationStorageCompressionMode | False | Named | False |
| EnableEncryption | Enables encryption for a specific application backup policy. Veeam Backup & Replication will encrypt the data that is passed between backup infrastructure components on the source and target side. | SwitchParameter | False | Named | False |
| EncryptionKey | Creates an encryption key for the specified application backup policy. | Accepts the VBREncryptionKey object. To define this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the VBRKMSServer object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSAPOnOracleStorageOptions object that defines SAP on Oracle storage settings.

Examples

Creating SAP on Oracle Storage Settings for Application Backup Policies for Veeam Plug-In for SAP on Oracle

This command creates an SAP on Oracle storage settings for application backup policies for Veeam Plug-In for SAP on Oracle. The policy will apply compression to backups using Oracle tools.

|  |
| --- |
| New-VBRSAPOnOracleStorageOptions -CompressionEnabled -CompressionMode RMAN |


