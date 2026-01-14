---
title: "cc_disk_restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_disk_restore.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can restore disks from tenant backups and attach them to a VM that runs on a virtualization host in the SP infrastructure. To perform the disk restore operation, the SP must use Veeam PowerShell cmdlets — this operation is not available in the SP Veeam backup console.

Prerequisites and limitations for disk restore on the SP side are the same as in the regular Veeam backup infrastructure. For details, see the [Performing Instant Disk Recovery: Before You Begin](https://helpcenter.veeam.com/docs/vbr/userguide/instant_disk_recovery_before_you_begin.html?ver=13) section in the Veeam Backup & Replication User Guide.

In addition, for disk restore from tenant backups on the SP side consider the following:

* Tenant backups must be available on the SP side. For details, see [Restoring Data from Tenant Backups](cc_data_restore.md).
* The target virtualization host and VM where the SP plans to restore disks must be added to the Veeam Backup & Replication infrastructure on the SP backup server.
* Veeam Cloud Connect supports disk restore from unencrypted backups only.

To restore disks from a tenant backup, complete the following steps:

1. Disable the tenant account. For more information, see [Disabling and Enabling Tenant Accounts](cloud_connect_disable_account.md).
2. Run the Get-VBRCloudTenantBackup cmdlet to specify the backup from which you want to restore disks. For details, see the [Get-VBRCloudTenantBackup](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantbackup.html?ver=13) section in the Veeam PowerShell Reference.
3. Run the Get-VBRCloudTenantRestorePoint cmdlet to specify the necessary restore point in the backup. For details, see the [Get-VBRCloudTenantRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantrestorepoint.html?ver=13) section in the Veeam PowerShell Reference.
4. Run the Get-VBRServer and Find-VBRViEntity cmdlets to specify the target host and VM where you want to restore disks from the backup.
5. Run the Get-VBRViVirtualDevice cmdlet to specify the disks that you want to restore.
6. Run the Start-VBRViInstantVMDiskRecovery cmdlet to restore disks.

For example:

|  |
| --- |
| $backup = Get-VBRCloudTenantBackup -Name "Fileserver Backup to Cloud" |

For details, see the [Start-VBRViInstantVMDiskRecovery](https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrviinstantvmdiskrecovery.html?ver=13) section in the Veeam PowerShell Reference.

After Veeam Backup & Replication mounts the restored disk to the target VM, you must finalize the process. For details, see the [Finalizing Instant Disk Recovery](https://helpcenter.veeam.com/docs/vbr/userguide/instant_disk_recovery_finalize.html?ver=13) section in the Veeam Backup & Replication Guide and [Start-VBRViInstantRecoveryDiskMigration](https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrviinstantrecoverydiskmigration.html?ver=13) section in the Veeam PowerShell Reference.

Once you finalize the disk restore operation, you can enable the tenant account.

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
