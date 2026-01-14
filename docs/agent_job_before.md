---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_before.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a Veeam Agent backup job managed by the backup server in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers that you plan to add to the Veeam Agent backup job. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the job must be configured in advance.

Veeam Agent backup jobs have the following limitations:

* You can store backups created by a Veeam Agent backup job in a Veeam backup repository and Veeam Cloud Connect repository. If you want to save backups in other target locations, you must configure a Veeam Agent backup job managed by Veeam Agent (backup policy). To learn more, see [Creating Policy for Windows Computers](agent_policy_create_win.md).
* Veeam Agent for Microsoft Windows does not support file-level backup for backup jobs that include failover clusters.
* Veeam Agent for Microsoft Windows does not back up data to which symbolic links are targeted. It only backs up the path information that the symbolic links contain. After restore, identical symbolic links are created in the restore destination.

* You cannot map a Veeam Agent backup job managed by the backup server to a Veeam Agent backup chain created by another type of a Veeam Agent backup job. After you change the mode of a Veeam Agent computer, Veeam Backup & Replication starts a new backup chain in a target location specified in the backup job settings.

* The backup cache is not supported for Veeam Agent backup jobs managed by backup server.
* Veeam Agent does not support creating transaction log backups in a cloud repository. You cannot enable transaction log backup options in the properties of the backup job targeted at a cloud repository.

* You cannot add a Veeam Agent computer protected by a Veeam Agent backup policy to a backup job managed by the backup server. To add such a computer to a backup job managed by the backup server, first remove the computer from the Veeam Agent backup policy.

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
