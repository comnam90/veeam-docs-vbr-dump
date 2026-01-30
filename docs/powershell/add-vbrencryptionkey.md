---
title: "Add-VBREncryptionKey"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrencryptionkey.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Add-VBREncryptionKey


Short Description

Creates encryption key.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBREncryptionKey -Password <securestring> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new encryption key.

This cmdlet accepts SecureString type. Use Microsoft PowerShell standard capabilities to convert your password into the SecureString.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Password | Specifies password you want to use to encrypt data. | SecureString | True | 0 | True (ByValue, ByProperty Name) |
| Description | Specifies description of the new encryption key that you can further use to search encryption keys. | String | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[PSCryptoKey](pscryptokey.md)

Examples

Creating Encryption Key

This command creates the Veeam Administrator encryption key.

|  |
| --- |
| $plainpassword = "VeeamPassword"  $securepassword = $plainpassword | ConvertTo-SecureString -AsPlainText -Force  Add-VBREncryptionKey -Password $securepassword -Description "Veeam Administrator" |

Perform the following steps:

1. Save the password into the $plainpassword variable.
2. Turn the password into a SecureString by running the [ConvertTo-SecureString](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.4) command. Provide the AsPlainText and Force parameters.
3. Run the Add-VBREncryptionKey cmdlet. Set the $securepassword variable as the Password parameter value. Specify the Description parameter value.


