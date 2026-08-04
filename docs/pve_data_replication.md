---
title: "Performing Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_data_replication.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Replication


To produce VM replicas, Veeam Backup & Replication runs replication jobs. A replication job is a collection of settings that define the way replication operations are performed: what data to replicate, where to store replicas, when to start the replication process, and so on.

One replication job can be used to process multiple VMs, but you can replicate each VM with one replication job at a time. If a VM is added to more than one replication job, it will be processed only by the replication job that started earlier.

In This Section

* [Creating Replication Jobs](pve_replication_job_create.md)
* [Retrying Replication Jobs](pve_replication_job_retry.md)
* [Editing Replication Jobs](pve_replication_job_edit.md)
* [Cloning Replication Jobs](pve_replication_job_clone.md)
* [Disabling and Enabling Replication Jobs](pve_replication_job_disable.md)
* [Deleting Replication Jobs](pve_replication_job_delete.md)

Page updated 2026-07-27

