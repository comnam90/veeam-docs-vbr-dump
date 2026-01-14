---
title: "Get-VBRMoveBackupSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrmovebackupsession.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Get-VBRMoveBackupSession

In this article

Short Description

Returns move sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all move sessions.

|  |
| --- |
| Get-VBRMoveBackupSession [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Get move sessions for the specified backup.

|  |
| --- |
| Get-VBRMoveBackupSession -Backup <VBRBackup> [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Get a move session with a specific session ID.

|  |
| --- |
| Get-VBRMoveBackupSession -Id <Guid> [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Get move sessions for the specified machine.

|  |
| --- |
| Get-VBRMoveBackupSession -MachineName <String> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet returns move sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backup for which you want to get move sessions. | Accepts the VBRBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | False |
| Id | Specifies the ID of the session. The cmdlet will return the session with this ID. | Guid | True | Named | False |
| MachineName | Specifies the name of the machine for which you want to return the move sessions. | String | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMoveBackupSession[] object that contains settings of the move session.

Examples

Getting Move Sessions for Specific Backup

This example shows how to look for move sessions for the Cloud Webservices Backup backup job.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Cloud Webservices Backup"  Get-VBRMoveBackupSession -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Provide the Name parameter value. Save the result to the $backup variable.
2. Run the Get-VBRMoveBackupSession cmdlet. Set the $backup variable as the Backup parameter value.

Related Commands

[Get-VBRBackup](get-vbrbackup.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
