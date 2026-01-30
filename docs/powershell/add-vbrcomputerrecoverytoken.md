---
title: "Add-VBRComputerRecoveryToken"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcomputerrecoverytoken.html"
last_updated: "12/9/2025"
product_version: "13.0.1.1071"
---

# Add-VBRComputerRecoveryToken


Short Description

Creates tokens for bare-metal recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRComputerRecoveryToken -Backup <CBackup[]> [-ExpirationDate <DateTime>] [-FriendlyName <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates tokens that you can use to perform bare-metal recovery.

|  |
| --- |
| Important |
| You can not create tokens for Veeam Agent backups located in Veeam Cloud Connect repositories. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backups. The cmdlet will use a token to perform bare-metal recovery from these backups. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| ExpirationDate | Specifies the expiration date of a token. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| FriendlyName | Specifies a token friendly name. The cmdlet will create a token with this name. If you do not specify a friendly name, the cmdlet will create a default friendly name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerRecoveryToken object that contains tokens for bare-metal recovery.

Examples

Creating Token for Bare-Metal Recovery

This example shows how to create a token that you can use to perform bare-metal recovery. The friendly name is Win2049 token and the token will expire on 02.18.2023 at 12.00.00 AM.

|  |
| --- |
| $backup = Get-VBRBackup  $expirationDate = Get-Date -Year 2023 -Month 2 -Day 18 -Hour 0 -Minute 0 -Second 0  Add-VBRComputerRecoveryToken -Backup $backup[3] -ExpirationDate $expirationDate -FriendlyName "Win2049 token"  Name           : Recovery token 2022-10-18T23:29:07.992 for Backup Job 1  RecoveryToken  : EBe0-7e8e-72a6-3Eb2  ExpirationDate : 2/18/2023 12:00:00 AM  Backup         : {Backup Job 1}  FriendlyName   : Win2049 token |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $expirationDate variable.
3. Run the Add-VBRComputerRecoveryToken cmdlet. Set the $backup variable as the Backup parameter value. Set the $expirationDate variable as the ExpirationDate parameter value. Specify the FriendlyName parameter value.

The Get-VBRBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup (in our example, it is the fourth backup in the array).

The cmdlet output will contain the following details on the token: Name, RecoveryToken, ExpirationDate, Backup and FriendlyName.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


