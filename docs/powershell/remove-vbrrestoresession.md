---
title: "Remove-VBRRestoreSession (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrrestoresession.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRRestoreSession (obsolete)

In this article

Short Description

Removes restore sessions.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRRestoreSession -Session <CRestoreSession[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected restore session from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session you want to remove. | Accepts the CRestoreSession[] object. To get this object, run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Last Restore Session [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the last restore session of the Fileserver 03 VM.  |  | | --- | | Get-VBRRestoreSession -Name "Fileserver 03" | Select -Last 1 | Remove-VBRRestoreSession |  Perform the following steps:   1. Run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Select cmdlet. Specify the Last parameter value. 3. Pipe the cmdlet output to the Remove-VBRRestoreSession cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Selected Restore Session [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the Fileserver 03 restore session.  |  | | --- | | $session = Get-VBRRestoreSession -Name "Fileserver 03"  Remove-VBRRestoreSession -Session $session |  Perform the following steps:   1. Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet. Specify the Name parameter value. Save the result to the $session variable. 2. Run the Remove-VBRRestoreSession cmdlet. Set the $session as the Session parameter value. |

Related Commands

[Get-VBRRestoreSession](get-vbrrestoresession.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
