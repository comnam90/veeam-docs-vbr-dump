---
title: "Retention Policy for Quick Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/quick_backup_retention.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# Retention Policy for Quick Backups


When you perform a quick backup, Veeam Backup & Replication creates a single VM incremental restore point. Unlike a regular incremental restore point that contains data for all VMs in a job, single VM incremental restore point contains data only for a specific VM.

A single VM restore point is not considered a full-fledged restore point in the backup chain. From the retention policy perspective, a single VM restore point is grouped with the regular restore point that precedes it. When Veeam Backup & Replication needs to delete a single VM restore point due to retention, it waits until the preceding regular restore point expires — effectively extending retention by one VM restore point temporarily. Once the preceding regular restore point expires, Veeam Backup & Replication deletes both the regular restore point and the single VM restore point.

Starting from Veeam Backup & Replication 13, all new backup chains use the per-machine backup chain format by default. In this format, retention behaves slightly differently: the retention increases by the number of VMs from this chain for which quick backup was performed. It applies to the forward incremental and reverse incremental backup chains.


