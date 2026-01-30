---
title: "Performing Quick Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/performing_quick_backup_hv.html"
last_updated: "2/18/2025"
product_version: "13.0.1.1071"
---

# Performing Quick Backup


You can create an ad-hoc incremental backup for one or more VMs — quick backup, and add it to the backup chain in the backup repository. A quick backup is useful when you want to produce an additional restore point for one or more VMs in the backup job and do not want to configure a new job or modify the existing one.

Quick backup can be performed for VMs that meet the following requirements:

* A backup job processing the VM exists on the backup server.
* A full backup file for the VM exists in the backup repository configured in the backup infrastructure.

To perform a quick backup:

1. Open the Inventory view.
2. In the infrastructure tree, select a host or VM container (Hyper-V host, cluster, SCVMM, SCVMM tag, SCVMM host group, VM group, or volume) where the VMs you want to back up reside.
3. In the working area, select the VMs and click Quick Backup on the ribbon. You can also right-click the VMs and select Quick Backup.

Veeam Backup & Replication will trigger a backup job to create a new incremental restore point for each selected VM. Details of a running quick backup task are displayed in the job session window.

[![Click to zoom in](images/create_quick_backup_hv.webp)](images/create_quick_backup_hv.webp "Click to zoom in")


