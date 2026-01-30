---
title: "Get-VBREntraIDLogsBackupFLRItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidlogsbackupflritem.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDLogsBackupFLRItem


Short Description

Returns backed-up objects created by a log backup job.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREntraIdLogsBackupFLRItem -Session <VBRUnstructuredBackupFLRSession> [-Name <String>] [-Folder <VBRUnstructuredBackupFLRFolder>] [-Recurse]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up objects created by a log backup job. These objects contain settings of log files and folders backed up by a log backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will return backed-up objects within this restore session. | Accepts the VBRUnstructuredBackupFLRSession object. To create this object, run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies a name of the backed-up object. The cmdlet will return folders and files with the specified name.  Note: By default, the cmdlet returns up to 10,000 records (folders and files). You can change the default value with a registry key. For more information, contact [Veeam Customer Support](https://www.veeam.com/de/support.html?ad=menu-support). | String | False | Named | False |
| Folder | Specifies a backed-up folder. The cmdlet will return objects that are added to this folder. | Accepts the VBRUnstructuredBackupFLRFolder object. To get this object, run the Get-VBREntraIDLogsBackupFLRItem cmdlet. | False | Named | False |
| Recurse | Defines that the cmdlet will look for objects that are added to backed-up child folders.  If you provide this parameter, the cmdlet will return an array of all objects that are added to backed-up child folders. Otherwise, the cmdlet will return an array of objects that are added to the parent folder. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of VBRUnstructuredBackupFLRItem objects that contain settings of log files and folders backed up by the log backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting First-Level Log Folders

|  |  |
| --- | --- |
| This example shows how to get first-level log folders.  |  | | --- | | $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant  $folders = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession |  Perform the following steps:   1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.   The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.   1. Run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. Set the $logBackups[0] variable as the Backup parameter value. Set the $tenant variable as the Tenant parameter value. Save the result to the $logRestoreSession variable. 2. Run the Get-VBREntraIDLogsBackupFLRItem cmdlet. Set the $logRestoreSession variable as the Session parameter value. Save the result to the $folders variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Backed-Up Log Files and Folders

|  |  |
| --- | --- |
| This example shows how to get all backed-up log files and folders.  |  | | --- | | $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant  $filesFolders = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession -Recurse |  Perform the following steps:   1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.   The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.   1. Run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. Set the $logBackups[0] variable as the Backup parameter value. Set the $tenant variable as the Tenant parameter value. Save the result to the $logRestoreSession variable. 2. Run the Get-VBREntraIDLogsBackupFLRItem cmdlet. Specify the following settings:  * Set the $logRestoreSession variable as the Session parameter value. * Provide the Recurse parameter. * Save the result to the $filesFolders variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Files

|  |  |
| --- | --- |
| This example shows how to get audit and sign-in log files whose names start with 2024-11-01T10.  |  | | --- | | $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant  $files = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession -Name "2024-11-01T10\*" -Recurse |  Perform the following steps:   1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.   The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.   1. Run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. Set the $logBackups[0] variable as the Backup parameter value.Set the $tenant variable as the Tenant parameter value. Save the result to the $logRestoreSession variable. 2. Run the Get-VBREntraIDLogsBackupFLRItem cmdlet. Specify the following settings:  * Set the $logRestoreSession variable as the Session parameter value. * Specify the Name parameter value. * Provide the Recurse parameter value. * Save the result to the $files variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Logs from Specific Folder

|  |  |
| --- | --- |
| This example shows how to get all files that are located in the the Audit Logs folder. The Audit Logs folder is located in the November 2024 folder.  |  | | --- | | $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  $logBackups = Get-VBREntraIDLogsBackup  $logRestoreSession = Start-VBREntraIDLogsBackupFLRSession -Backup $logBackups[0] -Tenant $tenant  $novemberFolder = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession -Name "November 2024"  $auditLogsFolder = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession -Folder $novemberFolder -Name "Audit Logs"  $novAuditLogs = Get-VBREntraIDLogsBackupFLRItem -Session $logRestoreSession -Folder $auditLogsFolder |  Perform the following steps:   1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet.   The Get-VBREntraIDLogsBackup cmdlet will return an array of backups. Mind the ordinal number of the necessary backup, for arrays it starts with 0. In our example, it is the first backup in the array.   1. Run the [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md) cmdlet. Set the $logBackups[0] variable as the Backup parameter value. Set the $tenant variable as the Tenant parameter value. Save the result to the $logRestoreSession variable. 2. Run the Get-VBREntraIDLogsBackupFLRItem cmdlet. Set the $logRestoreSession variable as the Session parameter value. Specify the Name parameter value. Save the result to the $novemberFolder variable. 3. Run the Get-VBREntraIDLogsBackupFLRItem cmdlet. Specify the following settings:  * Set the $logRestoreSession variable as the Session parameter value. * Set the $novemberFolder variable as the Folder parameter value. * Specify the Name parameter value. * Save the result to the $auditLogsFolder variable.  1. Run the Get-VBREntraIDLogsBackupFLRItem cmdlet. Specify the following settings:  * Set the $logRestoreSession variable as the Session parameter value. * Set the $auditLogsFolder variable as the Folder parameter value. * Save the result to the $novAuditLogs variable. |

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md)
* [Start-VBREntraIDLogsBackupFLRSession](start-vbrentraidlogsbackupflrsession.md)


