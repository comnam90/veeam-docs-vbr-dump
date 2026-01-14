---
title: "cc_disk_publish"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_disk_publish.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can publish disks from tenant backups and mount them to a server added to the SP Veeam Backup & Replication infrastructure. To perform the disk publishing operation, the SP must use Veeam PowerShell cmdlets — this operation is not available in the SP Veeam backup console.

|  |
| --- |
| Tip |
| The disk publishing operation is also available on the tenant side. To publish disks, the tenant can use the Veeam backup console. To learn more, see [Publishing Disks](publishing_disks.md). |

Prerequisites and limitations for disk publishing on the SP side are the same as in the regular Veeam backup infrastructure. For details, see the [Disk Publishing (Data Integration API)](https://helpcenter.veeam.com/docs/vbr/userguide/data_integration_api.html?ver=13) section in the Veeam Backup & Replication User Guide.

Also keep in mind that Veeam Cloud Connect supports disk publishing from unencrypted backups only.

To publish disks from a tenant backup, complete the following steps:

1. Disable the tenant account. For more information, see [Disabling and Enabling Tenant Accounts](cloud_connect_disable_account.md).
2. Run the Get-VBRCloudTenantBackup cmdlet to get the backup from which you want to restore disks. For details, see the [Get-VBRCloudTenantBackup](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantbackup.html?ver=13) section in the Veeam PowerShell Reference.
3. Run the Get-VBRCloudTenantRestorePoint cmdlet to get the necessary restore point in the backup. For details, see the [Get-VBRCloudTenantRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantrestorepoint.html?ver=13) section in the Veeam PowerShell Reference.
4. Run the Publish-VBRBackupContent cmdlet to publish disks.

For example:

|  |
| --- |
| $backup = Get-VBRCloudTenantBackup -Name "Fileserver Backup to Cloud" |

For more information, see the [Publish-VBRBackupContent](https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrbackupcontent.html?ver=13) section in the Veeam PowerShell Reference.

The disk content will become available in the C:\VeeamFLR\ folder on the target server. For disks of Microsoft Windows machines, the disk content is available in the read-only state. You can perform the necessary operations with the published disk data, for example, find specific documents, copy files or perform antivirus scan of the backed-up data.

After you finish working with the disk content, you can stop the disk publishing session. For details, see the [Managing Published Disks](https://helpcenter.veeam.com/docs/vbr/userguide/publishing_disks_manage.html?ver=13) section in the Veeam Backup & Replication Guide and [Unpublish-VBRBackupContent](https://helpcenter.veeam.com/docs/vbr/powershell/unpublish-vbrbackupcontent.html?ver=13) section in the Veeam PowerShell Reference.

Once the disk publishing session is stopped, you can enable the tenant account.

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
