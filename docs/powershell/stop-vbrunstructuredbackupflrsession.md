---
title: "Stop-VBRUnstructuredBackupFLRSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrunstructuredbackupflrsession.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRUnstructuredBackupFLRSession

In this article

Short Description

Stops restore sessions started to recover backups created by file backup jobs or object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRUnstructuredBackupFLRSession -Session <VBRUnstructuredBackupFLRSession> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops restore sessions started to recover backups created by file backup jobs or object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will stop this restore session. | Accepts the VBRUnstructuredBackupFLRSession object. To get this object, run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Stopping Restore Session Running to Recover Unstructured Data

This example shows how to stop a restore session that is started to recover backups created by file backup jobs and object storage backup jobs.

|  |
| --- |
| $session = Get-VBRUnstructuredBackupFLRSession  Stop-VBRUnstructuredBackupFLRSession -Session $session |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet. Save the result to the $session variable.
2. Run the Stop-VBRUnstructuredBackupFLRSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md)

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
