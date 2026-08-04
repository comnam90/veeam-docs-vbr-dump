---
title: "Start-VBRApplicationBackupCopyInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrapplicationbackupcopyinstantrecovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRApplicationBackupCopyInstantRecovery


Short Description

Starts instant recovery of the application backup repository data from a backup copy restore point.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRApplicationBackupCopyInstantRecovery -RestorePoint <COib> -Server <CHost> -RestoreFolder <String> [-Reason <String>] [-RepositoryPermissions <VBRApplicationBackupRepositoryPermission[]>] [-EnableKerberosPermissions] [-KerberosPermissions <VBRApplicationBackupRepositoryKerberosPermission[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an instant recovery session from the backup copy restore point of the application backup repository data. Veeam Backup & Replication mounts the restore point to the temporary folder on the application backup repository host and makes the application data immediately available via NFS.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the backup copy restore point from which you want to start instant recovery of the application backup repository data. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Server | Specifies the application backup repository host on which Veeam Backup & Replication will mount the restore point data via NFS. | Accepts the [CHost](chost.md) object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| RestoreFolder | Specifies the temporary NFS mount path to which Veeam Backup & Replication will mount the backup copy restore point. | String | True | Named | False |
| Reason | Specifies the reason for starting instant recovery. The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RepositoryPermissions | Specifies host permissions for accessing the temporary NFS share. | Accepts the [VBRApplicationBackupRepositoryPermission](vbrapplicationbackuprepositorypermission.md)[] object. To create this object, run the [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) cmdlet. | False | Named | False |
| EnableKerberosPermissions | Enables Kerberos authentication for accessing the temporary NFS share. | SwitchParameter | False | Named | False |
| KerberosPermissions | Specifies permissions for accessing the temporary NFS share with Kerberos credentials. | Accepts the [VBRApplicationBackupRepositoryKerberosPermission](vbrapplicationbackuprepositorykerberospermission.md)[] object. To create this object, run the [New-VBRKerberosPermission](new-vbrkerberospermission.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will start instant recovery without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSession object that contains information about the instant recovery session.

Examples

Starting Instant Recovery from Backup Copy Restore Point

This example shows how to start instant recovery of the application backup repository data from a backup copy restore point.

|  |
| --- |
| $restorePoint = Get-VBRRestorePoint -Name "ApplicationBackup01"  $server = Get-VBRServer -Name "172.18.21.25"  $permission = New-VBRApplicationBackupRepositoryPermission -ServerName "172.18.21.26" -Mode ReadWrite  Start-VBRApplicationBackupCopyInstantRecovery -RestorePoint $restorePoint -Server $server -RestoreFolder "/ApplicationBackup01\_restore" -RepositoryPermissions $permission |

Perform the following steps:

* Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorePoint variable.
* Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
* Run the [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) cmdlet. Specify the ServerName and Mode parameter values. Save the result to the $permission variable.
* Run the Start-VBRApplicationBackupCopyInstantRecovery cmdlet. Specify the following settings:

* Set the $restorePoint variable as the RestorePoint parameter value.
* Set the $server variable as the Server parameter value.
* Specify the RestoreFolder parameter value.
* Set the $permission variable as the RepositoryPermissions parameter value.

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md)
* [New-VBRKerberosPermission](new-vbrkerberospermission.md)

Page updated 2026-06-04

