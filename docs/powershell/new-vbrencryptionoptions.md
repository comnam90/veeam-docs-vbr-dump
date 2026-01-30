---
title: "New-VBREncryptionOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrencryptionoptions.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# New-VBREncryptionOptions


Short Description

Defines encryption settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define encryption options with the disabled encryption.

|  |
| --- |
| New-VBREncryptionOptions [-EnableEncryption]  [<CommonParameters>] |

* Define encryption options with the encryption using an encryption key.

|  |
| --- |
| New-VBREncryptionOptions [-EnableEncryption] -EncryptionKey <VBREncryptionKey>  [<CommonParameters>] |

* Define encryption options with the encryption using a KMS server.

|  |
| --- |
| New-VBREncryptionOptions [-EnableEncryption] -KMSServer <VBRKMSServer> -KMSSourceName <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBREncryptionOptions object that defines encryption options.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EncryptionKey | Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt backup files. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | True (ByPropertyName) |
| KMSServer | Specifies the KMS server you want to use to encrypt the data. | Accepts the VBRKMSServer object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| KMSSourceName | Specifies the displayed name for the key. The cmdlet will create a key and include this name into the key name on the KMS server. | String | False | Named | False |
| EnableEncryption | Enables encryption.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREncryptionOptions](vbrencryptionoptions.md) object that defines encryption options.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Encryption Options with Encryption Key

|  |  |
| --- | --- |
| This example shows how to define encryption options with the encryption using an encryption key.  |  | | --- | | $encKey = Get-VBREncryptionKey -Description "For Entra ID encryption"  $encOptions = New-VBREncryptionOptions -EnableEncryption -EncryptionKey $encKey |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $encKey variable. 2. Run the New-VBREncryptionOptions cmdlet. Provide the EnableEncryption parameter. Set the $encKey variable as the EncryptionKey parameter value. Save the result to the $encOptions variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Encryption Options with KMS

|  |  |
| --- | --- |
| This example shows how to define encryption options with the encryption using a KMS server.  |  | | --- | | $kmsServer = Get-VBRKMSServer -Name "thales.tech.local"  $encOptions = New-VBREncryptionOptions -EnableEncryption -KMSSourceName "EntraIDKey" -KMSServer $kmsServer |  Perform the following steps:   1. Run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. Specify the Name parameter value. Save the result to the $kmsServer variable. 2. Run the New-VBREncryptionOptions cmdlet. Specify the following settings:  * Provide the EnableEncryption parameter. * Specify the KMSSourceName parameter. * Set the $kmsServer variable as the KMSServer parameter value. * Save the result to the $encOptions variable. |

Related Commands

* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [Get-VBRKMSServer](get-vbrkmsserver.md)


