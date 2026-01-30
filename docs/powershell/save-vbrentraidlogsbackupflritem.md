---
title: "Save-VBREntraIDLogsBackupFLRItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/save-vbrentraidlogsbackupflritem.html"
last_updated: "2/27/2025"
product_version: "13.0.1.1071"
---

# Save-VBREntraIDLogsBackupFLRItem


Short Description

Restores files and folders backed up by a log backup job that protects Microsoft Entra ID audit and sign-in logs.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Save-VBREntraIDLogsBackupFLRItem -Server <VBRUnstructuredServer> -Item <VBREntraIDLogsBackupFLRItem[]> -Path <String> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores and saves files and folders backed up by a log backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of Entra ID log files and folders that you want to restore. | Accepts the VBREntraIDLogsBackupFLRItem[] object. To get this object, run the [Get-VBREntraIDLogsBackupFLRItem](get-vbrentraidlogsbackupflritem.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Server | Specifies the file share to which you want to restore log files or folders. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folder where you want to restore log files or folders. | String | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of VBRUnstructuredBackupFLRItem objects that contain settings of restored log files and folders.

Examples

Restoring Log Files

This example shows how to restore the log files whose names start with 2024-11-01T10. The files are restored to the \\WinSrv\Reports file share to the \\WinSrv\Reports\Restored folder.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant  $fileshare = Get-VBRUnstructuredServer -Name "\\WinSrv\Reports"  $files = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession -Name "2024-11-01T10\*" -Recurse  Save-VBREntraIDLogsBackupFLRItem -Server $fileshare -Item $files -Path "\\WinSrv\Reports\Restored" |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.

The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.

1. Run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. Set the $logBackups[0] variable as the Backup parameter value. Set the $tenant variable as the Tenant parameter value. Save the result to the $logRestoreSession variable.
2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $fileshare variable.
3. Run the [Get-VBREntraIDLogsBackupFLRItem](get-vbrentraidlogsbackupflritem.md) cmdlet. Specify the following settings:

* Set the $logRestoreSession variable as the Session parameter value.
* Specify the Name parameter value.
* Provide the Recurse parameter value.
* Save the result to the $files variable.

1. Run the Save-VBREntraIDLogsBackupFLRItem cmdlet. Specify the following settings:

* Set the $files variable as the Item parameter value.
* Set the $fileshare variable as the Server parameter value.
* Specify the Path parameter value.

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md)
* [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md)
* [Get-VBREntraIDLogsBackupFLRItem](get-vbrentraidlogsbackupflritem.md)


