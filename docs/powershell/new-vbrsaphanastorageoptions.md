---
title: "New-VBRSAPHANAStorageOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsaphanastorageoptions.html"
last_updated: "7/2/2025"
product_version: "13.0.1.1071"
---

# New-VBRSAPHANAStorageOptions


Short Description

Creates the SAP HANA storage encryption settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSAPHANAStorageOptions [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates SAP HANA storage encryption settings that apply to application backup policies for Veeam Plug-In for SAP HANA.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableEncryption | Enables encryption for a specific application backup policy. Veeam Backup & Replication will encrypt the data that is passed between backup infrastructure components on the source and target side. | SwitchParameter | False | Named | False |
| EncryptionKey | Creates an encryption key for the specified application backup policy. | Accepts the VBREncryptionKey object. To define this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the VBRKMSServer object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSAPHANAStorageOptions object that defines SAP HANA database storage settings.

Examples

Creating SAP HANA Application Backup Policy Encryption Key

This command enables the encryption for a specified SAP HANA application backup policy and creates an encryption key.

|  |
| --- |
| New-VBRSAPHANAStorageOptions -EnableEncryption -EncryptionKey $key  $key = Get-VBREncryptionKey -Description "Veeam Administrator" |

Perform the following steps:

1. Run the New-VBRSAPHANAStorageOptions cmdlet. Use the EnableEncryption parameter. Set the $key variable as the EncryptionKey parameter value.
2. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter. Save the result to the $key variable.

Related Commands

* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [Get-VBRKMSServer](get-vbrkmsserver.md)


