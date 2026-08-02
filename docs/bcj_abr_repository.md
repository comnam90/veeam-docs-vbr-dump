---
title: "Backup Copy Jobs for Application Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/bcj_abr_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Copy Jobs for Application Backup Repositories


In addition to saving application backup repository data to snapshots, you can configure a backup copy job to copy the data to a secondary backup repository.

Unlike other backup copy jobs, the backup copy job for application backup repositories does not mirror data from the source repository. This backup copy job transforms snapshot restore points into a regular backup chain of full and incremental backups. Subsequently, you can archive these backups to tape using backup to tape jobs. For more information, see [Backup to Tape](backup_to_tape_jobs.md).

When the backup copy job for application backup repositories runs for the first time, it creates a full backup file (VBK) from the latest repository snapshot. For subsequent incremental backups (VIB), Veeam Backup & Replication compares two latest snapshots on the application backup repository side, sends only the changed blocks to the target repository, and verifies the data integrity of the resulting backup chain.

The backup copy job allows you to restore the application backup repository data to any alternative application backup repository host, for example, if the original repository is lost. During the restore process, Veeam Backup & Replication will export the application backup repository data to a temporary NFS share for browsing and selective restore. For more information, see [Performing Application Backup Repository Restore from Backup Copy](abr_restore_bcj.md).

Limitations for Backup Copy Jobs for Application Backup Repositories

Before you run a backup copy job or an application backup repository restore from a backup copy job, consider the following limitations:

* For backup copy jobs for application backup repositories, you cannot select the [Veeam Cloud Connect repository](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_configure_repository.html) as a backup copy target.
* The backup copy job is temporarily paused once you start the restore process for one of its restore points.
* If the source application backup repository has been recovered using the Revert snapshot mode, on the next run, the backup copy job creates a full restore point.
* If the last backup copy job run was more than 90 days ago, the next incremental run of this job will fail. Veeam Backup & Replication will prompt you to create an active full backup to restart the backup chain.

Removing Stuck Network Block Devices

During a backup copy job or an application backup repository restore from a backup copy job, Veeam Backup & Replication attaches network block devices on the application backup repository host. In some cases — for example, if the job stops unexpectedly or the network connection drops — these devices may fail to detach properly and remain in a stuck state. If a network block device remains stuck, subsequent runs of the backup copy job may fail. To clean up such network block devices for an application backup repository, do the following:

1. Log in to the Veeam Host Management web UI as a Host Administrator. For details, see [Accessing Veeam Host Management Console](hmc_access.md).
2. In the management pane, click Backup Infrastructure.
3. In the Application Backup Repository section, click Remove next to Use this option to clean up stuck network block devices.

Related Topics

* [Creating Backup Copy Jobs for Application Backup Repositories](create_bcj_abr.md)
* [Performing Application Backup Repository Restore from Backup Copy](abr_restore_bcj.md)
* [Backup to Tape](backup_to_tape_jobs.md)

Page updated 2026-07-29

