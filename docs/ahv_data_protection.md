---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_data_protection.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Performing Backup


To produce VM backups, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup job can be used to process multiple VMs, but you can back up each VM with one backup job at a time. If a VM is added to more than one backup job, it will be processed only by the backup job that started earlier.

|  |
| --- |
| Note |
| To back up data that resides on Nutanix Files, use the Veeam Backup & Replication file share backup functionality described in section [Unstructured Data](unstructured_data_backup.md). |


