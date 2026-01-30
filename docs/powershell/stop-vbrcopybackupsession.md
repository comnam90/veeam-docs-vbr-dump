---
title: "Stop-VBRCopyBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrcopybackupsession.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRCopyBackupSession


Short Description

Specifies how to process backups for which a copy session failed.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRCopyBackupSession [-ActionType {DetachFailed | Undo}] [-RunAsync] -Session <VBRCopyBackupSession> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet specifies how to process backups for which a copy session failed.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the copy session that failed (has the User action required status). | Accepts the VBRCopyBackupSession object. To get this object, run the [Get-VBRCopyBackupSession](get-vbrcopybackupsession.md) cmdlet. | True | Named | False |
| ActionType | Specifies what to do:   * DetachFailed: do not copy backups for which the session failed. * Undo: cancel all changes the copy session made. | VBRBackupMoveCopySessionStopAction | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSession object that contains settings of the copy session.


