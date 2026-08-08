---
title: "Performing Backup Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_backup_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup Using Web UI


Backup appliances run backup policies for every data protection operation. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup policy can be used to process multiple resources within different regions, but you can back up each resource with one backup policy at a time. For example, if an instance is added to more than one backup policy, it will be processed only by a backup policy that has the highest priority. For information on how to set a priority for a backup policy, see section [Setting Backup Policy Priority](azure_backup_policy_priority.md). Other backup policies will skip this instance from processing.

In This Section

* [Performing VM Backup](azure_performing_vm_backup.md)
* [Performing SQL Backup](azure_performing_sql_backup.md)
* [Performing Azure Files Backup](azure_performing_fs_backup.md)
* [Performing Cosmos DB Backup](azure_performing_cosmos_db_backup.md)
* [Performing Virtual Network Configuration Backup](azure_performing_vnet_backup.md)
* [Managing Backup Policies](azure_managing_policies.md)

Page updated 2026-07-01

