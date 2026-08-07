---
title: "Start-VBREntraIDLogsBackupFLRSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrentraidlogsbackupflrsession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBREntraIDLogsBackupFLRSession


Short Description

Starts a restore session to explore log files and folders that a log backup contains.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREntraIDLogsBackupFLRSession -Backup <VBREntraIdLogsBackup> -Tenant <VBREntraIDTenant>  [<CommonParameters>] |

Detailed Description

This cmdlet starts a log restore session. During this session, the cmdlet gets access to the log files and folders in the Entra ID log backup.

After you gain the access, you can use this session to restore specific files and folders stored in the log backup. For this, launch the following cmdlets:

* [Get-VBREntraIDLogsBackupFLRItem](get-vbrentraidlogsbackupflritem.md) to get the backed-up files and folders.
* [Save-VBREntraIDLogsBackupFLRItem](save-vbrentraidlogsbackupflritem.md) to save the backed-up files and folders.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Backup | Specifies the backup from which you want to get access to logs. You can further restore files from this backup. | Accepts the VBREntraIdLogsBackup object. To get this object, run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Tenant | Specifies the tenant whose logs you want to access. | Accepts the VBREntraIDTenant object. To get this object, run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. | True | Named | True (ByPropertyName) |
| RetrievalSettings | Specifies the retrieval policy settings. The cmdlet will use these settings to retrieve data from archive repositories. | Accepts the VBRUnstructuredBackupColdStorageRetrievalSettings object. To create this object, run the [New-VBRUnstructuredBackupColdStorageRetrievalSettings](new-vbrunstructuredbackupretrievalsettings.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will modify settings of managed file shares without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRSession object that contains properties of the log restore session.

Examples

Starting Log Restore Session

This example shows how to start a log restore session.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.

The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.

1. Run the Start-VBREntraIDLogsBackupFLRSession cmdlet. Specify the following settings:

* Set the $logBackups[0] variable as the Backup parameter value.
* Set the $tenant variable as the Tenant parameter value.

* Save the result to the $logRestoreSession variable.

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md)
* [New-VBRUnstructuredBackupColdStorageRetrievalSettings](new-vbrunstructuredbackupretrievalsettings.md)

Page updated 2026-06-29

