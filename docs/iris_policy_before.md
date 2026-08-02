---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_policy_before.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you create an application backup policy in the Veeam Backup & Replication console, consider the following prerequisites and limitations:

* The Veeam Backup & Replication license must have a sufficient number of instances to process the IRIS instances that you plan to add to the application backup policy. For details, see [Licensing](iris_plan_and_manage_licensing.md).
* ODB servers, IRIS instances, file systems, backup proxies and storage systems must meet the system requirements. Veeam Backup & Replication supports only Linux-based backup proxies and USAPI-compatible storage systems. For details, see [System Requirements](iris_plan_and_manage_requirements.md).
* The storage system that hosts the IRIS data volumes must be registered in Veeam Backup & Replication with the Block storage for application protection role. For details, see [Registering Storage System for Application Protection](iris_storage_registration.md).
* A protection group for the ODB servers that you want to add to the policy must be configured and rescanned in advance. During the rescan, Veeam Backup & Replication discovers the IRIS instances available for backup. For details, see [Creating Protection Group for InterSystems IRIS Databases](iris_protection_group_create.md).
* If you run the policy in backup mode, the target backup repository must have enough free space for the backup files. In snapshot-only mode, Veeam Backup & Replication keeps the data as storage snapshots on the storage system and does not copy it to a backup repository.
* The policy does not process the journal (log) files of the IRIS instance. As a result, point-in-time restore is not available. Incremental backups use changed .DAT blocks. You can restore only to the state captured in a backup or storage snapshot. For details, see [Backup Types](iris_backup_types.md).

Page updated 2026-07-28

