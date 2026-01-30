---
title: "Stop-VBREntraIDLogsBackupFLRSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrentraidlogsbackupflrsession.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Stop-VBREntraIDLogsBackupFLRSession


Short Description

Stops a restore session started to recover data from Microsoft Entra ID log backups.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBREntraIDLogsBackupFLRSession -Session <VBRUnstructuredBackupFLRSession> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops a restore sessions started to recover a Entra ID log backup.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session that you want to stop. | Accepts the VBRUnstructuredBackupFLRSession object. To create this object, run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. To get this object, run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Entra ID Log Restore Session

This example shows how to stop a log restore session.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant  ...  Stop-VBREntraIDLogsBackupFLRSession -Session $logRestoreSession |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.

The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.

1. Run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. Specify the following settings:

* Set the $logBackups[0] variable as the Backup parameter value.
* Set the $tenant variable as the Tenant parameter value.

* Save the result to the $logRestoreSession variable.

1. Run the Stop-VBREntraIDLogsBackupFLRSession cmdlet. Set the $logRestoreSession variable as the Session parameter value.

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md)
* [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md)


