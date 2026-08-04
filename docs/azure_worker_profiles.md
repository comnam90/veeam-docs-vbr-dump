---
title: "Managing Worker Profiles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_profiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Worker Profiles


A profile is the VM size of a worker instance that backup appliances launch in a specific Azure region to perform a backup, restore, retention, archive, file share indexing, repository synchronization or health check operation. Backup appliances launch one worker instance per each Azure resource added to a backup policy or restore task.

Out of the box, backup appliances come with the default set of worker profiles where the primary profile is Standard\_F2s\_v2 and the archive profile is Standard\_E2\_v5. However, to boost operational performance, you can add custom sets of worker profiles to specify VM sizes of worker instances that will operate in different regions. When configuring worker profiles, you can choose the profile of each launched worker instance depending on the performed operation and the total size of the processed data:

Managing Worker Profiles

| Worker Profile | Default Azure VM Size | Usage |
| Small | Standard\_F2s\_v2 | * Backup and restore of the following workloads:  * Azure VMs whose total disk size is less than 100 GB * Azure SQL databases whose total size is less than 1 GB * Cosmos DB for PostgreSQL clusters whose total size is less than 22 GB  * File-level recovery of Azure VMs * Retention of backup chains whose total size is less than 100 GB, or whose length is less than 100 restore points * Repository synchronization, file share indexing and health check |
| Medium | Standard\_F4s\_v2 | * Backup and restore of the following workloads:  * Azure VMs whose total disk size is between 100 GB and 1 TB * Azure SQL databases whose total size is between 1 GB and 50 GB * Cosmos DB for PostgreSQL clusters whose total size is between 22 GB and 112 GB  * Retention of backup chains whose total size is between 100 GB and 1024 GB, or whose length is between 100 and 250 restore points |
| Large | Standard\_F8s\_v2 | * Backup and restore of the following workloads:  * Azure VMs whose total disk size is more than 1 TB * Azure SQL databases whose total size is more than 50 GB * Cosmos DB for PostgreSQL clusters whose total size is more than 112 GB  * Retention of backup chains whose total size is more than 1024 GB, or whose length is more than 250 restore points |
| Archiving | Standard\_E2\_v5 | * Backup archiving * Data retrieval operations |

In This Section

* [Adding Worker Profiles](azure_worker_profile_add.md)
* [Editing Worker Profiles](azure_worker_profile_edit.md)
* [Removing Worker Profiles](azure_worker_profile_remove.md)

Page updated 2026-07-01

