---
title: "Getting Started"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_getting_started.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Getting Started


To protect InterSystems IRIS instances with Veeam Backup & Replication, perform the following operations:

1. Register the storage system that hosts the InterSystems IRIS data volumes with the Block storage for application protection role. For more information, see [Registering Storage System for Application Protection](iris_storage_registration.md).
2. Create a protection group for InterSystems IRIS. For more information, see [Creating Protection Group](iris_protection_group_create.md).
3. Create an application backup policy to define what data you want to back up and configure backup settings. For more information, see [Creating Application Backup Policy](iris_policy_create.md).
4. Run the backup policy to create a backup and store it in the backup repository. To learn more, see [Starting and Stopping Application Backup Policy](iris_policy_manage_start_stop.md#start).
5. In case of a disaster, you can restore data from a backup. For more information, see [Restoring Backup from Snapshot](iris_restore_from_snapshot.md).

Page updated 2026-05-29

