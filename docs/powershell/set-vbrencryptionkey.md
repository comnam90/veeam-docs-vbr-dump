---
title: "Set-VBREncryptionKey"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrencryptionkey.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBREncryptionKey

In this article

Short Description

Modifies encryption key.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBREncryptionKey -EncryptionKey <PSCryptoKey> [-Password <securestring>] [-Description <string>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies encryption key that was created before.

This cmdlet accepts SecureString type. Use Microsoft PowerShell standard capabilities to convert your password into the SecureString.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EncryptionKey | Specifies the encryption key you want to modify. | Accepts the [PSCryptoKey](pscryptokey.md) object or string (description). To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | 0 | 0 | True (ByValue, ByProperty Name) |
| Password | Specifies the new password you want to apply to the encryption key. | SecureString | False | Named | False |
| Description | Specifies the new description you want to apply to the encryption key. | String | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[PSCryptoKey](pscryptokey.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Description of Encryption Key

|  |  |
| --- | --- |
| This example shows how to modify description of the Veeam Administrator encryption key.  |  | | --- | | Get-VBREncryptionKey -Description "Veeam Administrator" | Set-VBREncryptionKey -Description "Veeam Tape Backup Administrator" |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. 2. Pipe the cmdlet output to the Set-VBREncryptionKey cmdlet. Specify the Description parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting New Password to Encryption Key

|  |  |
| --- | --- |
| This example shows how to set a new password for the Veeam Administrator encryption key.  |  | | --- | | $plainpassword = "VeeamPassword"  $securepassword = $plainpassword | ConvertTo-SecureString -AsPlainText -Force  Get-VBREncryptionKey -Description "Veeam Administrator" | Set-VBREncryptionKey -Password $securepassword |  Perform the following steps:   1. Save the password as the $plainpassword variable. 2. Run the [ConvertTo-SecureString](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.4) cmdlet. Provide the AsPlainText and Force parameters. Save it to the $securepassword variable. 3. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. 4. Pipe the cmdlet output to the Set-VBREncryptionKey cmdlet. Set the $securepassword variable as the Password parameter value. |

Related Commands

[Get-VBREncryptionKey](get-vbrencryptionkey.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
