---
title: "Background Retention"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/background_retention_job_hv.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---

# Background Retention

In this article

In addition to applying a retention policy ([short-term retention](retention_policy_hv.md) and [long-term retention](gfs_retention_policy_hv.md)) within a job session, Veeam Backup & Replication performs background retention for backups. The background retention aims mostly at backups that are no longer processed by jobs (orphaned backups shown in the node with the (Orphaned) postfix). However, this retention can also be helpful for standard backups, in case backups are created by jobs without a schedule, the job retention has not been applied yet or failed for some reason, and so on.

The background retention starts automatically every 24 hours at 00:30, runs in the background and consists of the following activities:

* Background basic retention
* Background GFS retention
* Background log retention
* Backup cleanup
* Deleted Agent retention

Limitations

The background retention does not apply to the following backups:

* Backups stored on [backup repositories with rotated drives](backup_repository_rotated.md).
* Backups stored in the [archive tiers](archive_tier.md) of scale-out backup repositories.
* Backups stored in the [capacity tier](capacity_tier.md). For details, see section [Considerations](#Considerations).
* [Imported backups](importing_backups_hv.md).
* Replicas (including CDP replicas).
* [VeeamZIP backups](veeamzip.md).
* [Exported backups](exporting_backups_hv.md).
* [Copied backups](copy_backup_hv.md).

* Backups exported by [Kasten policies](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13).

* Backups created by [Veeam Plug-Ins for Enterprise Applications](protect_applications.md) and Veeam Cloud Plug-Ins ([Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*, [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)).

\* Available only for Miscrosoft Windows-based backup servers.

Considerations

Consider the following:

* Like the job retention, the background retention cannot delete immutable backup files. The background retention waits until the immutability and retention periods end for these files.

* [For backups linked to jobs] If the retention is set in days, Veeam Backup & Replication leaves at least 3 backup files in a backup chain regardless of the set retention. If the retention is set in restore points, Veeam Backup & Replication leaves backup files in a backup chain. The minimum number of backup files left equals the current retention period. You can delete these backup files manually as described in section [Deleting Backups from Disk](delete_backup_from_disk_hv.md).

* [For orphaned backups] If the retention is set in days, Veeam Backup & Replication can remove all outdated backup files in a backup chain. If the retention is set in restore points, Veeam Backup & Replication leaves backup files in a backup chain. The minimum number of backup files left equals the current retention period. To learn how to delete these backup files manually, see section [Deleting Backups from Disk](delete_backup_from_disk_hv.md).

* [For backups stored in the capacity tier] Background retention job does not delete capacity tier copies of backup data directly. However, if background retention removes local copies of backups, they may also be marked for removal on the capacity tier. In such a case, cleanup during the next SOBR offloading session will remove them from the capacity tier.
* [For backups created with Veeam Agent for Windows operating in standalone or managed by Veeam Agent mode] For backups linked to jobs basic retention does not apply.
* Unlike the job retention, the background retention does not merge data from one backup file to another; it just deletes files. In the case of forever forward incremental and forward incremental backup chains, the background retention deletes incremental files only after the last increment in the related part of the backup chain becomes outdated.
* The background retention does not delete backup files if they are locked by other processes. The retention waits until the backup file is unlocked.
* You can launch the background retention manually as described in section [Launching Background Retention](backup_background_retention_launch_hv.md).

Background Basic Retention

Background basic retention process analyzes the retention period set for backup files. In the case of orphaned backups, Veeam Backup & Replication analyzes the retention period that was set in the job that created this backup. If the retention period has expired, Veeam Backup & Replication removes the backup files.

Background GFS Retention

Background GFS retention process detects backup files with GFS flags and analyzes their retention period. If the retention period for GFS flags of such backup files has expired, Veeam Backup & Replication removes GFS flags. Then Veeam Backup & Replication deletes these backup files according to the short-term retention policy if the following conditions are met:

* The backup file does not have any other GFS flags assigned.
* The backup file does not have any dependent files.

Background retention job applies to backup files created by all types of jobs that use GFS. For more information about GFS retention policy, see [Long-Term Retention Policy (GFS)](gfs_retention_policy_hv.md).

Background Log Retention

Background log retention detects logs whose related image-level backup was deleted by background retention. Then Veeam Backup & Replication deletes these log files.

Backup Cleanup

Backup cleanup applies only to orphaned backups. After the whole orphaned backup chain is deleted, Veeam Backup & Replication also deletes the .VBM file and the folder where the backup chain was stored.

Deleted Agent Retention

Deleted agent retention is a process that detects and deletes outdated backup files according to Veeam Agent retention policy for outdated backups.

An outdated backup file is a backup file for which no new restore points were created and no new backup job sessions were started within the last N days, where N is the retention period specified in the Veeam Agent backup job settings.

For more information, see the [Retention Policy for Outdated Backups](https://helpcenter.veeam.com/docs/agentforwindows/userguide/retention_deleted_items.html?ver=13) article in the [Veeam Agent for Microsoft Windows](agents_introduction.md) User Guide and the [Maintenance Settings](agent_policy_advanced_maintain.md) article in Veeam Agent Backup.

Cloud Connect Background Retention

In the Veeam Cloud Connect infrastructure, background retention is applied to tenant backups on the service provider side. The background retention job runs automatically in Veeam Backup & Replication on the service provider backup server according to the same rules as in the regular Veeam backup infrastructure. The service provider can also launch background retention manually as described in section [Launching Background Retention](backup_background_retention_launch_hv.md).

On the tenant side, Veeam Cloud Connect repositories are skipped from processing by the background retention job launched automatically and manually. For more information, see the [Background Retention for Tenant Backups](https://helpcenter.veeam.com/docs/vbr/cloud/cc_background_retention.html?ver=13) section in the Veeam Cloud Connect Guide.

Related Links

* [Launching Background Retention](backup_background_retention_launch_hv.md)
* [Disabling Background Retention](backup_background_retention_disable_hv.md)

Page updated 11/27/2025

Page content applies to build 13.0.1.1071
