---
title: "Retry-VBRMoveBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/retry-vbrmovebackupsession.html"
last_updated: "4/9/2024"
product_version: "13.0.1.1071"
---

# Retry-VBRMoveBackupSession


Short Description

Retries the move operation for failed workloads.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Retry-VBRMoveBackupSession -Session <VBRMoveBackupSession> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet retries the move operation for failed workloads.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the move session which you want to retry. | Accepts the VBRCopyBackupSession object. To get this object, run the [Move-VBRBackup](move-vbrbackup.md) cmdlet. | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMoveBackupSession object that contains settings of the move session.

Examples

Retrying Move Operation

This example shows how to retry the move operation for failed workloads.

|  |
| --- |
| $backup = Get-VBRBackup  $repository = Get-VBRBackupRepository  $session = Move-VBRBackup -Backup $backup -Repository $repository  Retry-VBRMoveBackupSession -Session $session |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the [Move-VBRBackup](move-vbrbackup.md) cmdlet. Set the $backup variable as the Backup parameter value. Set the $repository variable as the Repository parameter value. Save the result to the $session variable.
4. Run the Retry-VBRMoveBackupSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Move-VBRBackup](move-vbrbackup.md)


