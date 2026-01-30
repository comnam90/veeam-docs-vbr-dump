---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_job_before_you_begin.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create a file backup job, consider the following:

* Backup infrastructure components that will take part in the file backup process must be added to the backup infrastructure and properly configured. These include source file shares to back up, backup proxies, and all repositories, including cache, backup and archive repositories. For more information, see the [Backup Infrastructure for Unstructured Data Backup](unstructured_data_backup_infrastructure.md) section.
* The target backup repository must have enough free space to store created backup files. If you want to receive notifications on the repository running low on free space, configure global notification settings as described in the [Specifying Global Notification Settings](global_notifications.md) section.
* Make sure that repositories intended to store file share backups are not configured to store files in the WORM status. Otherwise, the backup jobs will fail when Veeam Backup & Replication cannot update the backup metadata files.
* If you plan to map a file backup job to a backup that already exists in the backup repository, you must perform the rescan operation for this backup repository. Otherwise, Veeam Backup & Replication will not be able to recognize backup files in the backup repository.

For more information on how to rescan backup repositories, see the [Rescanning Backup Repositories](rescanning_backup_repositories.md) section.

* Antivirus software may significantly slow down file backup jobs. To improve performance, we recommend you exclude the c:\Program Files (x86)\Veeam\Backup Transport\x64\VeeamAgent.exe process from the antivirus scan on machines running the file backup proxy and backup repository roles. Keep in mind that it can weaken the security of these machines.

|  |
| --- |
| Note |
| If the objects that you want to back up were marked by the antivirus software as infected, the file backup job will be finished with the Warning or Failed state. The state will depend on the backed-up object. |

* Veeam Backup & Replication does not create the separate node in the inventory pane for the archived backups. If you use archive repositories and want to make sure that backups were moved to it, you can do it using backup properties. For more information, see [Viewing Unstructured Data Backup Properties](unstructured_data_backup_view_properties.md).
* If you plan to store backups in [Veeam Data Cloud Vault](osr_adding_veeam_data_cloud_vault.md), you must enable encryption.
* You cannot use the capacity tier of [scale-out backup repositories](backup_repository_sobr.md) as a target for file backup jobs.
* If you plan to use pre-job and post-job scripts, you must create scripts before you configure the file backup job.

* [For Linux-based backup server] The following applies to pre-job and post-job scripts:

* Bash scripts must use Linux-style line ednings (LF).
* Only the .SH and .PS1 file extensions are supported.

* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

To upload scripts to the Linux backup server, in the Veeam Backup & Replication console, navigate to the Files node. Then, copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.


