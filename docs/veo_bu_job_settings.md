---
title: "Required Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veo_bu_job_settings.html"
last_updated: "12/1/2025"
product_version: "13.0.1.1071"
---

# Required Job Settings


The required job settings depend on whether you want to use an image-level backup created with native Veeam Backup & Replication functionality or an application backup created with Veeam Plug-In for Oracle RMAN.

Image-Level Backups

When you create backup jobs, replication jobs, and CDP policies, make sure to enable application-aware processing in the Veeam Backup & Replication console.

You can configure this setting at the Specify Guest Processing Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see [Specify Guest Processing Settings](backup_job_vss_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console.

Without application-aware processing, the created restore points will be crash-consistent only.

For more information about configuring archive log backup, see the Oracle Archived Redo Log Settings step of the job or policy wizard for the relevant hypervisor, cloud or physical platform. For example, see [Oracle Archived Redo Log Settings](backup_job_vss_oracle_vm.md) for VMware vSphere backup jobs started in the Veeam Backup & Replication console.

Veeam Explorer for Oracle allows you to explore crash-consistent restore points with heuristic analysis, which scans the restore point for application data. Note that application item restore from crash-consistent restore points is less reliable than restore from application-consistent restore points. Without application-aware processing, the restore point could contain unfinished database transactions or incomplete application files, which may affect data recovery.

Consider the following:

* For backups made with [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/data_protection.html) and [Veeam Plug-in for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/data_protection.html), application-aware processing is not supported.
* For VeeamZIP backups, application-aware processing is not supported. For more information, see [VeeamZIP](veeamzip.md).
* For storage snapshots, application-aware processing is automatically enabled. For more information, see [Application Item Restore from Storage Snapshots](restore_veeam_explorers_snapshots.md).

For details on how to explore restore points created without application-aware processing, see [Exploring non-Application Enabled Backups](veor_exploring_nonvss.md).

The application-specific information is retrieved according to the following logic:

* If the application-aware processing is enabled, Veeam Explorer for Oracle obtains application-specific Oracle database information from the backup metadata located in the backup server configuration database.

* If the application-aware processing is disabled, Veeam Explorer for Oracle requires a staging Oracle server to mount the selected image-level backup (with databases and redo logs) and to collect required information using the guest scan and Oracle infrastructure analysis.

|  |
| --- |
| Important |
| Consider the following:   * Make sure to have your database in the OPEN state during backup. Otherwise, the following warning message will appear in the backup job session: Oracle database instance state is not valid for property collection. * Whether the backup job completes or fails depends on the selected backup job settings. For more information, see [Enable Application-Aware Processing](backup_job_vss_application_vm.md). |

Backups Created with Veeam Plug-In for Oracle RMAN

You can create backups of Oracle databases using application backup policies managed by Veeam Backup & Replication and backup jobs managed by a standalone Veeam Plug-In for Oracle RMAN.

* To create an application backup policy managed by Veeam Backup & Replication, do the following:

1. Add the source Oracle machine to a protection group. For more information, see [Creating Protection Group for Individual Computers](protection_group_individual.md).
2. Create an application backup policy using the protection group. For more information, see [Creating Oracle RMAN Backup Policy](create_policy_create_oracle_rman.md).

* To create a backup job managed by a standalone Veeam Plug-In for Oracle RMAN, you can use native Oracle RMAN functionality. For more information, see [Database Protection](rman_protection.md).

After the RMAN plug-in backups are successfully created using one of these methods, you can use Veeam Explorer for Oracle to restore your Oracle data.


