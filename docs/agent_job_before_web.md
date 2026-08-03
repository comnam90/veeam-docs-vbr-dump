---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_before_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you create a Veeam Agent backup job managed by the backup server in the Veeam Backup & Replication web UI, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers and workstations that you plan to add to the Veeam Agent backup job. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the job must be configured in advance.

Veeam Agent backup jobs have the following limitations:

* You can store backups created by a Veeam Agent backup job in a Veeam backup repository. If you want to save backups in other target locations, you must configure a Veeam Agent backup job managed by Veeam Agent (backup policy). To learn more, see [Creating Policy for Windows Computers](agent_policy_create_win_web.md).

|  |
| --- |
| NOTE |
| The Veeam Cloud Connect repository is not supported as a backup destination in the Veeam Backup & Replication web UI. |

* Veeam Agent for Microsoft Windows does not support file-level backup for backup jobs that include failover clusters.
* Veeam Agent for Microsoft Windows does not back up data to which symbolic links are targeted. It only backs up the path information that the symbolic links contain. After restore, identical symbolic links are created in the restore destination.

* The backup cache is not supported for Veeam Agent backup jobs managed by backup server.

* You cannot add a Veeam Agent computer protected by a Veeam Agent backup policy to a backup job managed by the backup server. To add such a computer to a backup job managed by the backup server, first remove the computer from the Veeam Agent backup policy.

Page updated 2026-07-14

