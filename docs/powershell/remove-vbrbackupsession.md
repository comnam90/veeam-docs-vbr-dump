---
title: "Remove-VBRBackupSession (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrbackupsession.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRBackupSession (obsolete)

In this article

Short Description

Removes a specified backup session.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Remove-VBRBackupSession -Session <CBackupSession[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes specified backup session from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the backup session you want to remove.  You can assign multiple sessions to this object. | Accepts the CBackupSession[] object. To get this object, run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Selected Backup Session [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the Fileserver Backup backup session.  |  | | --- | | Get-VBRBackupSession -Name "Fileserver Backup" | Remove-VBRBackupSession |  Perform the following steps:   1. Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRBackupSession cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Selected Backup Session [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the Fileserver Backup backup session.  |  | | --- | | $FileserverBackup = Get-VBRBackupSession -Name "Fileserver Backup"  Remove-VBRBackupSession -Session $FileserverBackup |  Perform the following steps:   1. Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet. Specify the Name parameter value. 2. Run the Remove-VBRBackupSession cmdlet. Set the $FileserverBackup as the Session parameter value. |

Related Commands

[Get-VBRBackupSession](get-vbrbackupsession.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
