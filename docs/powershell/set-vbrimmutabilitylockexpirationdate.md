---
title: "Set-VBRImmutabilityLockExpirationDate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrimmutabilitylockexpirationdate.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Set-VBRImmutabilityLockExpirationDate


Short Description

Modifies immutability period of restore points located in a hardened repository.

|  |
| --- |
| Important |
| This cmdlet does not support the following types of restore points:   * Restore points created by [unstructured data source jobs](working_unstructured_source.md). * Restore points created by [application backup policies](plugin_management.md). * Restore points for transaction logs. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Extend immutability period of restore points located in a hardened repository.

|  |
| --- |
| Set-VBRImmutabilityLockExpirationDate -RestorePoint <COib[]> -ExpirationDate <datetime>  [<CommonParameters>] |

* Reset immutability period of restore points located in a hardened repository.

|  |
| --- |
| Set-VBRImmutabilityLockExpirationDate -RestorePoint <COib[]> -ToOriginal  [<CommonParameters>] |

Detailed Description

This cmdlet modifies immutability period of restore points located in a hardened repository.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Important |
| It is not possible to reduce immutability via PowerShell commands. After you set the value, you can either extend it or reset back to the original value. However, you cannot set it to a smaller value than was originally set. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies an array of restore points. The cmdlet will modify immutability period for these restore points. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| ExpirationDate | Specifies a date when Veeam Backup & Replication is allowed to remove restore points from a hardened repository with immutability. | DateTime | True | Named | False |
| ToOriginal | Defines that the cmdlet will reset the immutability period of restore points to their original value. If you provide this value, the cmdlet will set the immutability to the maximum time period that is available for the hardened repository.  Default: False. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRImmutabilityLockExpirationDate object that contains immutability period of of restore points located in hardened repository with immutability.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Extending Immutability Period of Restore Points

|  |  |
| --- | --- |
| This examples shows how to set Veeam Backup & Replication to remove restore points on 03.02.2023 from the hardened repository.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  $date = Get-Date -Year 2023 -Month 2 -Day 3 -Hour 0 -Minute 0 -Second 0  Set-VBRImmutabilityLockExpirationDate -RestorePoint $restorepoint -ExpirationDate $date |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $date variable. 3. Run the Set-VBRImmutabilityLockExpirationDate cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $date variable as the ExpirationDate parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Resetting Immutability Period of Restore Points

|  |  |
| --- | --- |
| This examples shows how to reset immutability period of restore points. The cmdlet will set the immutability to the time period that was originally specified for the hardened repository.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  Set-VBRImmutabilityLockExpirationDate -RestorePoint $restorepoint -ToOriginal |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Set-VBRImmutabilityLockExpirationDate cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Provide the ToOriginal parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


