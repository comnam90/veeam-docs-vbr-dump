---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_unix_before.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you create a Veeam Agent backup job managed by the backup server in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers that you plan to add to the Veeam Agent backup job. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).
* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the job must be configured in advance.
* If you want to configure a backup window for the job, make sure the computers are added to the job through protection groups. Backup window configuration is available only for computers in protection groups.

Veeam Agent backup jobs have the following limitations:

* You can create Veeam Agent backups in a Veeam backup repository only. If you want to save backups in other target locations, you must configure a Veeam Agent backup policy. To learn more, see [Creating Policy for Unix Computers](agent_policy_create_unix.md).
* You cannot map a Veeam Agent backup job managed by the backup server to a Veeam Agent backup chain created by another type of a Veeam Agent backup job. After you change the mode of a Veeam Agent computer, Veeam Backup & Replication starts a new backup chain in the target location specified in the backup job settings.
* You cannot add a Veeam Agent computer protected by a Veeam Agent backup policy to a backup job managed by the backup server. To add such a computer to a backup job managed by the backup server, first remove the computer from the Veeam Agent backup policy.
* If you want malware detection states to appear on Veeam Agent for Unix restore points in the Veeam Backup & Replication console, you must enable guest indexing in the [Guest Processing](agent_job_unix_guest.md) step of the wizard.

Page updated 2026-06-22

