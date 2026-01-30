---
title: "WAL Files PostgreSQL Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_backup_hiw_hv.html"
last_updated: "2/12/2025"
product_version: "13.0.1.1071"
---

# WAL Files PostgreSQL Backup Jobs


To maintain data consistency and integrity, Veeam Backup & Replication makes a backup of write ahead log (WAL) files for PostgreSQL instances. Veeam Backup & Replication uses these log files to recover PostgreSQL instances and bring them to the necessary consistent state.

To back up WAL files, you must create a backup job, add a PostgreSQL VM to it and specify advanced settings for WAL files in the job settings. The resulting job will consist of two jobs:

* Parent backup job — the job that creates an image-level backup of PostgreSQL VMs. You specify a parent backup job name when you define settings for a backup job, for example, Daily DB Job. For more information, see [Specify Job Name and Description](backup_job_name_hv.md). For more information on how image-level backup of PostgreSQL VMs works, see [Application-Aware Processing](application_aware_processing_hv.md#Linux).
* Child job — the job that creates a backup of WAL files. To form a name of the child job, Veeam Backup & Replication adds a suffix to the name of the parent backup job: <parent\_job\_name> + PostgreSQL Log Backup, for example, Daily Job PostgreSQL Log Backup. When Veeam Backup & Replication detects a backup job that contains at least one PostgreSQL VM, it automatically creates the child job to back up WAL files. Veeam Backup & Replication keeps session data of the child job in the configuration database and displays it in the console. For more information on how the job creates a backup of WAL files, see [How PostgreSQL WAL Files Backup Works](postgresql_backup_job_hv.md).

The parent job runs in a regular manner — it starts by schedule or is started manually by the user. The child job is triggered by the parent backup job. This sequence ensures that the VM (and the instances) restore point is present when you need to use WAL files to restore the database.

Sessions of Archived Log Backup Jobs

The child backup job runs permanently in the background, shipping WAL files to the backup repository at a specific time interval (by default, every 15 minutes). A sequence of time intervals between sessions of the parent backup job makes up a session of the child backup job.

The child backup session starts and stops in the following way:

* The initial session starts when the parent backup job schedule is enabled. After that, the session starts with every new session of the parent backup job.
* The session ends before the next session of the parent backup job or when this parent backup job is disabled.
* When the session ends, Veeam Backup & Replication stops the non-persistent runtime components and uninstalls them from the VM guest OS. When a new session starts, the runtime components are deployed again.


