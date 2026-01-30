---
title: "Get-VBRCopyBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcopybackupsession.html"
last_updated: "4/9/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCopyBackupSession


Short Description

Returns copy sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get copy sessions for the specified backup.

|  |
| --- |
| Get-VBRCopyBackupSession -Backup <VBRBackup> [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Get a copy session with a specific session ID.

|  |
| --- |
| Get-VBRCopyBackupSession -Id <Guid> [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Get copy sessions for the specified machine.

|  |
| --- |
| Get-VBRCopyBackupSession -MachineName <String> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet returns copy sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backup for which you want to get copy sessions. | Accepts the VBRBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | False |
| Id | Specifies the ID of the session. The cmdlet will return the session with this ID. | Guid | True | Named | False |
| MachineName | Specifies the name of the machine for which you want to return the copy sessions. | String | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCopyBackupSession[] object that contains settings of the copy session.

Examples

Getting Copy Sessions for Specific Backup

This command returns copy sessions for the Exchange Backup\_imported backup.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Exchange Backup\_imported"  Get-VBRCopyBackupSession -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Get-VBRCopyBackupSession cmdlet. Set the $backup variable as the Backup parameter value.

Related Commands

[Get-VBRBackup](get-vbrbackup.md)


