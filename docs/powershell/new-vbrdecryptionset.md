---
title: "New-VBRDecryptionSet"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrdecryptionset.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRDecryptionSet

In this article

Short Description

Defines data decryption settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Decrypt data encrypted by KMS server.

|  |
| --- |
| New-VBRDecryptionSet -EncryptionKey <PSCryptoKey> -KMSServer <VBRKMSServer> [-KmsKeyId <String>]  [<CommonParameters>] |

* Decrypt data using password.

|  |
| --- |
| New-VBRDecryptionSet -EncryptionKey <PSCryptoKey> -Password <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRDecryptionSet object. This object defines the data decryption settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EncryptionKey | Specifies encryption keys managed by Veeam Backup & Replication. | Accepts the PSCryptoKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the VBRKMSServer object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| KmsKeyId | Specifies the ID of the private key stored on the KMS server. The cmdlet will use it to decrypt data. | String | False | Named | True (ByPropertyName, ByValue) |
| Password | Specifies a password. The cmdlet will use the password to decrypt data. | String | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDecryptionSet](vbrdecryptionset.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Decryption Settings for Data Encrypted by KMS

|  |  |
| --- | --- |
| This example shows how to define settings to decrypt data encrypted by KMS server.  |  | | --- | | $key = Get-VBREncryptionKey -Description "Veeam KMS"  $kmsserver = Get-VBRKMSServer -Name "thales.tech.local"  $decryption = New-VBRDecryptionSet -EncryptionKey $key -KMSServer $kmsserver -KmsKeyId "c302ebfd-821c-4372-bf46-beccca0516ec-pub" |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $key variable. 2. Run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. Specify the Name parameter value. Save the result to the $kmsserver variable. 3. Run the New-VBRDecryptionSet cmdlet. Set the $key variable as the EncryptionKey parameter value. Set the $kmsserver variable as the KMSServer parameter value. Specify the KmsKeyId parameter value. Save the result to the $decryption variable to be used with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Data Decryption Settings with Password

|  |  |
| --- | --- |
| This example shows how to define settings to decrypt data using password.  |  | | --- | | $key = Get-VBREncryptionKey -Description "Veeam KMS"  $decryption = New-VBRDecryptionSet -EncryptionKey $key -Password "VeeamPassword" |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $key variable. 2. Run the New-VBRDecryptionSet cmdlet. Set the $key variable as the EncryptionKey parameter value. Specify the Password parameter value. Save the result to the $decryption variable to be used with other cmdlets. |

Related Commands

* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [Get-VBRKMSServer](get-vbrkmsserver.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
