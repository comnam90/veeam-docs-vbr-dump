---
title: "Start-VBRNASInstantRecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrnasinstantrecovery.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Start-VBRNASInstantRecovery

In this article

Short Description

Starts an instant restore of backups created by the file backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRNASInstantRecovery -RestorePoint <VBRUnstructuredBackupRestorePoint[]> [-Permissions <VBRNASPermissionSet[]>] [-MountOptions <VBRNASInstantRecoveryMountOptions>] [-Reason <string>] [-RunAsync] [-WaitAllSessions]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an instant restore of backups created by the file backup job. It starts agents, creates a file share on the specified repository (the file share name is retrieved from the file share backup) and creates records in the database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies an array of restore points. The cmdlet will start an instant recovery for each of the specified restore points. | Accepts the VBRUnstructuredBackupRestorePoint[] object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Permissions | Specifies an array of permission sets. The cmdlet will start an instant recovery by applying these permission sets. | Accepts the VBRNASPermissionSet[] object. To create this object, run the [New-VBRNASPermissionSet](new-vbrnaspermissionset.md) cmdlet. | False | 1 | False |
| MountOptions | Specifies a mapping configuration for instant restore of file backups.  If the parameter is not defined, the cmdlet will use automatic mapping. | Accepts the VBRNASInstantRecoveryMountOptions object. To create this object, run the [New-VBRNASInstantRecoveryMountOptions](new-vbrnasinstantrecoverymountoptions.md) cmdlet. | False | 2 | False |
| Reason | Specifies the reason for starting the instant restore of file backups. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WaitAllSessions | If the parameter is set to True, the cmdlet will wait for all sessions to finish before returning the result. In this case, the result is sorted according to the order in which restore points are specified. Sessions are also started in this order.  If the parameter is set to False, the cmdlet will return the result after each session finishes. In this case, the result is returned in nondeterministic order.  Note: This parameter is used with the RunAsync parameter that must be set to False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASInstantRecovery](vbrnasinstantrecovery.md)[] object that defines the following settings: session ID, backup name (the same as the job name), creation time of the used restore point, job type (it is always equal to EDbJobType.InstantFileShareRestore), ID and name of the mount server where the restore was started, UNC path of the published SMB share with file backup contents, session name, permission settings, mount state.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Instant Restore for File Backups with Automatic Mapping

|  |  |
| --- | --- |
| The following example shows how to start instant restore for file backups with automatic mapping.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasBackupPoint = Get-VBRUnstructuredBackupRestorePoint -NASBackup $backup  $permissions = New-VBRNASPermissionSet -RestorePoint $nasBackupPoint[0] -Owner "User 1" -AllowEveryone  Start-VBRNASInstantRecovery -RestorePoint $nasBackupPoint[0] -Permissions $permissions -Reason "Test instant restore for NAS" |   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the NASBackup parameter value. Save the result to the $nasBackupPoint variable. 3. Run the [New-VBRNASPermissionSet](new-vbrnaspermissionset.md) cmdlet. Specify the RestorePoint, Owner and AllowEveryone parameter values. 4. Run the Start-VBRNASInstantRecovery cmdlet. Specify the following parameters:  * Specify the first value from the array returned to the $nasBackupPoint variable as the RestorePoint parameter. * Set the $permissions variable as the Permissions parameter value. * Specify the Reason parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Instant Restore for File Backups with Manual Mapping

|  |  |
| --- | --- |
| The following example shows how to start instant restore for file backups with manual mapping.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasBackupPoint = Get-VBRUnstructuredBackupRestorePoint -NASBackup $backup  $permissions = New-VBRNASPermissionSet -RestorePoint $nasBackupPoint[0] -Owner "User 1" -AllowEveryone  $manualMapping = New-VBRNASInstantRecoveryMountOptions -RestorePoint $nasBackupPoint[0] -MountServer "172.17.20.3"  Start-VBRNASInstantRecovery -RestorePoint $nasBackupPoint[0] -Permissions $permissions -MountOptions $manualMapping -Reason "Test instant restore for NAS" |   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the NASBackup parameter value. Save the result to the $nasBackupPoint variable. 3. Run the [New-VBRNASPermissionSet](new-vbrnaspermissionset.md) cmdlet. Specify the RestorePoint, Owner and AllowEveryone parameter values. 4. Run the [New-VBRNASInstantRecoveryMountOptions](new-vbrnasinstantrecoverymountoptions.md) cmdlet. Specify the RestorePoint and MountServer parameter values.  1. Run the Start-VBRNASInstantRecovery cmdlet. Specify the following parameters:  * Specify the first value from the array returned to the $nasBackupPoint variable as the RestorePoint parameter. * Set the $permissions variable as the Permissions parameter value. * Set the $manualMapping variable as the MountOptions parameter value. * Specify the Reason parameter. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)
* [New-VBRNASPermissionSet](new-vbrnaspermissionset.md)
* [New-VBRNASInstantRecoveryMountOptions](new-vbrnasinstantrecoverymountoptions.md)

Page updated 9/4/2024

Page content applies to build 13.0.1.1071
