---
title: "How PostgreSQL WAL Files Backup Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_backup_job.html"
last_updated: "3/4/2025"
product_version: "13.0.1.1071"
---

# How PostgreSQL WAL Files Backup Works

In this article

To maintain integrity and data consistency, Veeam Backup & Replication makes a backup of write ahead log (WAL) files that contain PostgreSQL instance logs. Veeam Backup & Replication uses these log files for instance recovery operations.

To back up WAL files, you must enable application-aware processing for PostgreSQL VMs. After this, during the job session Veeam Backup & Replication installs non-persistent runtime components or uses (if necessary, installs) persistent agent components on this VM to collect information about the instance and process WAL files according to job settings. For more information on how to configure application-specific settings for PostgreSQL WAL files backup, see [PostgreSQL WAL Files Settings](backup_job_vss_postgresql_vm.md) step of the backup job wizard — you can specify how logs should be backed up and deleted for PostgreSQL instances.

The WAL files backup for PostgreSQL VMs is performed in the following way:

1. Veeam Backup & Replication launches the parent backup job by schedule.
2. The parent backup job creates an image-level backup of the PostgreSQL VM and stores this backup in the backup repository.
3. A child job starts to back up WALs: Veeam Backup & Replication accesses the PostgreSQL VM guest OS over SSH. By default, Veeam Backup & Replication installs non-persistent components to the VM guest OS, and Veeam Backup & Replication will uninstall them after the job completes. You can also install a Linux management agent to the VM guest OS — in this case, the agent will remain installed on the VM and Veeam Backup & Replication will use it to access the VM guest OS. For more information, see [Persistent Agent Components](persistent_agent_components.md).
4. Veeam Backup & Replication scans the PostgreSQL system and gets the necessary information to back up backup and restore a PostgreSQL instance.

* List of all databases added to the instance.

* The instance state — if the instance is on or off, in which logging mode it runs.
* Paths to all Instance files (configuration logs and so on) and other data required for backup.

1. The non-persistent runtime components or persistent agent components copy WALs from the log archive destination (set in the [guest processing settings](backup_job_vss_postgresql_vm.md) of a job) to a temporary directory on the VM guest file system.

1. Veeam Backup & Replication maps information about the PostgreSQL system collected at the step 4 with information kept in the configuration database. This periodic mapping helps to reveal instances for which Veeam Backup & Replication must ship WALs to the backup repository during this time interval.

1. Veeam Backup & Replication transfers WALs from the temporary location on the PostgreSQL VM to the backup repository and saves them as VLB files. Veeam Backup & Replication transfers WALs either directly or through the log shipping server. The source-side Veeam Data Mover compresses log data to be transferred according to its built-in settings. On the backup repository side, data is compressed according to the parent backup job settings.

1. Veeam Backup & Replication deletes WALs from the temporary directory on the VM guest file system.

|  |
| --- |
| Important |
| Consider the following:   * Veeam Backup & Replication removes only backed-up WALs from a temporary folder. The WALs that were not backed up during the log backup interval remain in the temporary folder. Veeam Backup & Replication will process these logs during the next log backup interval. * If a new session of the WALs backup starts and the parent backup job has not created a new restore point yet, the WALs backup job will remain in the idle state, waiting for a new restore point to be created. |

Page updated 3/4/2025

Page content applies to build 13.0.1.1071
