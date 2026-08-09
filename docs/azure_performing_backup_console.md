---
title: "Performing Backup Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_backup_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup Using Console


Veeam Backup & Replication runs backup policies for every data protection operation. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where backups will be stored, when the backup process will start, and so on.

You can create multiple backup policies for Azure resources. One backup policy can be used to process multiple resources within different regions, but you can back up each resource with one backup policy at a time. For example, if an instance is added to more than one backup policy, it will be processed only by a backup policy that has the highest priority. Other backup policies will skip this instance from processing. For information on how to set a priority for a backup policy, see section [Setting Backup Policy Priority](azure_backup_policy_priority.md).

After you install Veeam Plug-in for Microsoft Azure and add backup appliances to the backup infrastructure, you can manage backup policies directly from the Veeam Backup & Replication console.

In This Section

* [Creating Backup Policies](azure_backup_policy_add_console.md)
* [Editing Backup Policy Settings](azure_backup_policy_edit_console.md)
* [Enabling and Disabling Backup Policies](azure_backup_policy_enable_disable_console.md)
* [Starting and Stopping Backup Policies](azure_backup_policy_start_stop_console.md)
* [Deleting Backup Policies](azure_backup_policy_delete_console.md)
* [Creating Backup Copy Jobs](azure_backup_copy_console.md)
* [Copying Backups to Tapes](azure_copy_to_tape_console.md)

Page updated 2026-07-01

