---
title: "Performing Backup Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_performing_backup_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup Using Console


Veeam Backup & Replication runs backup policies for every data protection operation. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where backups must be stored, when the backup process must start, and so on.

You can create multiple backup policies for AWS resources. One backup policy can be used to process multiple resources within different regions, but you can back up each resource with one backup policy at a time. For example, if an instance is added to more than one backup policy, it will be processed only by a backup policy that has the highest priority. Other backup policies will skip this instance from processing. For information on how to set a priority for a backup policy, see [Settings Policy Priority](aws_policies_priority.md).

After you install Veeam Plug-in for AWS and add backup appliances to the backup infrastructure, you can manage backup policies directly from the Veeam Backup & Replication console.

In This Section

* [Creating Backup Policies](aws_add_policy.md)
* [Editing Backup Policy Settings](aws_editing_policies_settings.md)
* [Enabling and Disabling Backup Policies](aws_disabling_and_enabling_policies.md)
* [Starting and Stopping Backup Policies](aws_starting_and_stopping_policies.md)
* [Deleting Backup Policies](aws_deleting_policies.md)
* [Verifying Backups](aws_verify_backups.md)
* [Creating Backup Copy Jobs](aws_backup_copy.md)
* [Copying Backups to Tapes](aws_copy_to_tape.md)

Page updated 2026-05-21

