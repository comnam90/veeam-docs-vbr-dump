---
title: "Snapshot Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_retention_snapshots.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Snapshot Retention


For Proxmox VE replicas, you specify retention policy restore points. Veeam Backup & Replication retains the number of latest restore points defined in job scheduling settings as described in section [Creating Replicarion Jobs](pve_replication_job_create_settings.md).

During every successful replication session, Veeam Backup & Replication creates a new restore point. If Veeam Backup & Replication detects that the number of restore points in the snapshot chain exceeds the retention limit, it removes the earliest restore point from the chain.

![Snapshot Retention](images/pve_snapshot_retention.webp)

Page updated 2026-07-21

