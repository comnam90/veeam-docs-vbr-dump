---
title: "Stop-VBRNASBackupFLRSession (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrnasbackupflrsession.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRNASBackupFLRSession (obsolete)

In this article

Short Description

Stops restore sessions started to recover backups created by file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Stop-VBRUnstructuredBackupFLRSession](stop-vbrunstructuredbackupflrsession.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRNASBackupFLRSession -Session <VBRNASBackupFLRSession> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops restore sessions started to recover backups created by file backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will stop this restore session. | Accepts the VBRNASBackupFLRSession object. To get this object, run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Stopping Restore Sessions

This example shows how to stop a restore session that is started to recover backups created by file backup jobs.

|  |
| --- |
| $session = Get-VBRNASBackupFLRSession  Stop-VBRNASBackupFLRSession -Session $session |

Perform the following steps:

1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable.
2. Run the Stop-VBRNASBackupFLRSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
