---
title: "Set-VBRComputerRecoveryToken"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerrecoverytoken.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerRecoveryToken


Short Description

Modifies tokens for bare-metal recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerRecoveryToken -RecoveryToken <VBRComputerRecoveryToken[]> [-ExpirationDate <DateTime>] [-FriendlyName <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of tokens that you can use to perform bare-metal recovery.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RecoveryToken | Specifies an array of token. The cmdlet will modify these tokens. | Accepts the VBRComputerRecoveryToken[] object. To get this object, run the [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| ExpirationDate | Specifies the expiration date of a token. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| FriendlyName | Specifies a token friendly name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

|  |
| --- |
| Note |
| Since the cmdlet does not return any object, to view the changes you must run the [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md) cmdlet. |

Examples

Modifying Expiration Date of Tokens for Bare-Metal Recovery

This example shows how to modify an expiration date of tokens that you can use to perform bare-metal recovery. The cmdlet will set expiration date to 02.20.2023 at 12.00.00 AM.

|  |
| --- |
| $token = Get-VBRComputerRecoveryToken  $expirationDate = Get-Date -Year 2023 -Month 2 -Day 20 -Hour 0 -Minute 0 -Second 0  Set-VBRComputerRecoveryToken -RecoveryToken $token -ExpirationDate $expirationDate |

Perform the following steps:

1. Run the [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md) cmdlet. Save the result to the $token variable.
2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $expirationDate variable.
3. Run the Set-VBRComputerRecoveryToken cmdlet. Set the $token variable as the RecoveryToken parameter value. Set the $expirationDate variable as the ExpirationDate parameter value.

Related Commands

* [Get-VBRComputerRecoveryToken](get-vbrcomputerrecoverytoken.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


