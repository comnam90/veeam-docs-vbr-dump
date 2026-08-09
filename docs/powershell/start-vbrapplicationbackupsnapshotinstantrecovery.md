---
title: "Start-VBRApplicationBackupSnapshotInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrapplicationbackupsnapshotinstantrecovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRApplicationBackupSnapshotInstantRecovery


Short Description

Starts instant recovery from an application backup repository snapshot.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRApplicationBackupSnapshotInstantRecovery -Snapshot <VBRApplicationBackupSnapshot> -MountPath <String> [-Reason <String>] [-RepositoryPermissions <VBRApplicationBackupRepositoryPermission[]>] [-EnableKerberosPermissions] [-KerberosPermissions <VBRApplicationBackupRepositoryKerberosPermission[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an instant recovery session from an application backup repository snapshot. Veeam Backup & Replication mounts the snapshot to the temporary NFS path and makes the application data available for browsing and selective restore.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Snapshot | Specifies the snapshot to which you want to recover the application backup repository. Veeam Backup & Replication will mount the snapshot to export data. | Accepts the [VBRApplicationBackupSnapshot](vbrapplicationbackupsnapshot.md) object. To get this object, run the [Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md) cmdlet. | True | Named | False |
| MountPath | Specifies the temporary NFS path to which Veeam Backup & Replication will mount the application backup repository snapshot for browsing and selective restore. | String | True | Named | False |
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

Starting Instant Recovery from Application Backup Repository Snapshot

This example shows how to start instant recovery from an application backup snapshot and grant access to the NFS share for a specific host.

|  |
| --- |
| $snapshot = Get-VBRApplicationBackupSnapshot -Name "ApplicationBackupSnapshot01"  $permission = New-VBRApplicationBackupRepositoryPermission -ServerName "172.18.21.25" -Mode ReadWrite  Start-VBRApplicationBackupSnapshotInstantRecovery -Snapshot $snapshot -MountPath "dataset\_recovery" -RepositoryPermissions $permission |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable.
2. Run the [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md) cmdlet. Specify the ServerName and Mode parameter values. Save the result to the $permission variable.
3. Run the Start-VBRApplicationBackupSnapshotInstantRecovery cmdlet. Set the $snapshot variable as the Snapshot parameter value. Specify the MountPath parameter value. Set the $permission variable as the RepositoryPermissions parameter value.

Related Commands

* [Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md)
* [New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md)
* [New-VBRKerberosPermission](new-vbrkerberospermission.md)

Page updated 2026-06-08

