---
title: "Transaction Log Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sql_backup_job.html"
last_updated: "6/25/2024"
product_version: "13.0.1.1071"
---

# Transaction Log Backup Jobs


To back up transaction logs, you must create a backup job, add Microsoft SQL Server VMs to it and specify advanced settings for transaction log backup in the job settings. The resulting job will comprise two jobs:

* Parent backup job — the backup job that creates an image-level backup of the Microsoft SQL Server VM. The parent backup job is named <job\_name>, for example, DB Backup. You can configure the parent job in the Veeam Backup & Replication console just like any other backup job.
* Child job — a transaction log backup job. To form a name of the child job, Veeam Backup & Replication adds a suffix to the name of the parent backup job: <parent\_job\_name> + SQL Server Transaction Log Backup, for example, DB Backup SQL Server Transaction Log Backup. Veeam Backup & Replication automatically creates the child job if it detects a backup job that is scheduled to back up at least one Microsoft SQL Server VM, and transaction log backup is enabled for this job. Session data of the transaction log backup job is stored in the configuration database and displayed in the Veeam Backup & Replication console.

The parent job runs in a regular manner — it starts by schedule or is started manually by the user. The transaction log backup job is triggered by the parent backup job. This sequence ensures that the VM (and the database) restore point is present when it comes to transaction log replay.

Sessions of Transaction Log Backup Jobs

The transaction log backup job runs permanently in the background, shipping transaction logs to the backup repository at a specific time interval (by default, every 15 minutes). A sequence of time intervals between sessions of the parent backup job makes up a session of the transaction log backup job.

The transaction log backup session starts and stops in the following way:

* The initial session starts when the parent backup job schedule is enabled. After that, the session starts with every new session of the parent backup job.
* The session ends before the next session of the parent backup job or when this parent backup job is disabled.
* When the session ends, Veeam Backup & Replication stops the non-persistent runtime components and uninstalls them from the VM guest OS. When a new session starts, the runtime components are deployed again.


