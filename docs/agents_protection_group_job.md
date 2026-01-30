---
title: "Adding Protection Group to Backup Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protection_group_job.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Adding Protection Group to Backup Job


You can quickly add an entire protection group to a Veeam Agent backup job configured in Veeam Backup & Replication.

Before working with protection groups, consider the following limitations:

* You can add a protection group for pre-installed Veeam Agents only to a backup policy (Veeam Agent backup job managed by Veeam Agent). Veeam Agent backup jobs managed by the backup server are not supported by this type of protection groups. To learn more about backup job types, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).

* You can add a protection group for cloud machines only to a Veeam Agent backup job managed by the backup server. Backup policies are not supported by this type of protection group. To learn more about backup job types, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).
* You cannot add both cloud machines and physical computers to the same backup job.
* If you add a protection group that contains computers running different OSes to a Veeam Agent backup job for computers running a certain OS, Veeam Backup & Replication will automatically exclude computers running other OSes from this backup job.

For example, if you add protection group that contains Microsoft Windows, Linux, and Mac computers to a Veeam Agent backup job for Linux computers, Veeam Backup & Replication will automatically exclude Microsoft Windows and Mac computers from this backup job.

To add a protection group to a Veeam Agent backup job:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node and do one of the following:

For Microsoft Windows computers

* In the inventory pane, select the protection group that you want to add to the backup job and click Add to Backup > Windows > name of the job on the ribbon.
* In the inventory pane, right-click the protection group that you want to add to the backup job and select Add to backup job > Windows > name of the job.

For Linux computers

* In the inventory pane, select the protection group that you want to add to the backup job and click Add to Backup > Linux > name of the job on the ribbon.
* In the inventory pane, right-click the protection group that you want to add to the backup job and select Add to backup job > Linux > name of the job.

For Unix computers

* In the inventory pane, select the protection group that you want to add to the backup job and click Add to Backup > Unix > name of the job on the ribbon.
* In the inventory pane, right-click the protection group that you want to add to the backup job and select Add to backup job > Unix > name of the job.

[For protection groups for pre-installed Veeam Agents] For Mac computers

* In the inventory pane, select the protection group that you want to add to the backup job and click Add to Backup > Mac > name of the job on the ribbon.
* In the inventory pane, right-click the protection group that you want to add to the backup job and select Add to backup job > Mac > name of the job.

[![Add Protection Group to Backup Job](images/protection_group_job.webp)](images/protection_group_job.webp "Add Protection Group to Backup Job")


