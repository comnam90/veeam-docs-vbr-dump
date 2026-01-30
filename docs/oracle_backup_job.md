---
title: "Archived Log Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_backup_job.html"
last_updated: "3/4/2025"
product_version: "13.0.1.1071"
---

# Archived Log Backup Jobs


To back up archived logs, you must create a backup job, add Oracle VMs to it and specify advanced settings for archived logs backup in the job settings. The resulting job will comprise two jobs:

* Parent backup job — the backup job that creates an image-level backup of the Oracle VM. The parent backup job is named <job\_name>, for example, Daily Job. You can configure the parent job in the Veeam Backup & Replication console just like any other backup job.
* Child job — an archived log backup job. To form a name of the child job, Veeam Backup & Replication adds a suffix to the name of the parent backup job: <parent\_job\_name> + Oracle Redo Log Backup, for example, Daily Job Oracle Redo Log Backup. Veeam Backup & Replication automatically creates the child job if it detects a backup job that is scheduled to back up at least one Oracle VM, and archived log backup is enabled for this job. Session data of the archived log backup job is stored in the configuration database and displayed in the Veeam Backup & Replication console.

The parent job runs in a regular manner — it starts by schedule or is started manually by the user. The archived log backup job is triggered by the parent backup job. This sequence ensures that the VM (and the database) restore point is present when you need to use archived logs to restore the database.

Sessions of Archived Log Backup Jobs

The archived log backup job runs permanently in the background, shipping archived logs to the backup repository at a specific time interval (by default, every 15 minutes). A sequence of time intervals between sessions of the parent backup job makes up a session of the archived log backup job.

The archived log backup session starts and stops in the following way:

* The initial session starts when the parent backup job schedule is enabled. After that, the session starts with every new session of the parent backup job.
* The session ends before the next session of the parent backup job or when this parent backup job is disabled.
* When the session ends, Veeam Backup & Replication stops the non-persistent runtime components and uninstalls them from the VM guest OS. When a new session starts, the runtime components are deployed again.


