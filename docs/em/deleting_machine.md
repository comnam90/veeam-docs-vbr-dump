---
title: "Deleting Machine from Backup"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/deleting_machine.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Deleting Machine from Backup


When you delete a machine, it is not removed from the list of machines immediately. The machine will be removed after the records about the machine are removed from the configuration database on the backup server. Once this operation completes, a notification appears at the top of the Enterprise Manager window.

Before You Begin

Before you delete a machine from a backup, consider the following considerations and limitations:

* If four-eyes authorization is enabled on the backup server, you cannot delete a machine from backup using Enterprise Manager.
* If multiple machines are processed by the same backup job, deletion of a machine will not affect other machines in the job.
* The delete operation is not available for replica machines, storage snapshots and machines backed up to tape.

Deleting Machine

To delete a machine from a backup, do the following:

1. On the Machines tab, select the necessary machine backup from the list of machines.

To quickly find a machine, you can filter machines in the list by a backup server or search for specific machines by machine name.

1. Click Delete.
2. To remove backups marked with weekly, monthly and yearly GFS flags, select the Remove GFS full backups check box.

The check box is displayed if the machine has GFS backups.

1. Click Yes to confirm deletion.


