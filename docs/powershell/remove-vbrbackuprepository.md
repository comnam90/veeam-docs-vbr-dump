---
title: "Remove-VBRBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrbackuprepository.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRBackupRepository


Short Description

Removes a backup repository from the backup infrastructure.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRBackupRepository -Repository <CBackupRepository[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to remove a backup repository from the backup infrastructure.

When you remove a backup repository, Veeam Backup & Replication unassigns the repository role from the server, so it is no longer used as a backup destination. The actual server remains added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the array of backup repositories you want to remove. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Backup Repository [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the backup repository named Local Repository 01.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Local Repository 01"  Remove-VBRBackupRepository -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Remove-VBRBackupRepository cmdlet. Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Backup Repository [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the backup repository named Local Repository 01.  |  | | --- | | Get-VBRBackupRepository -Name "Local Repository 01" | Remove-VBRBackupRepository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRBackupRepository cmdlet. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)


