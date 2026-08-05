---
title: "Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_plan_and_manage_environment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Environment Planning


Before you deploy Veeam components and start protecting IRIS instances, keep in mind the following requirements and limitations:

* IRIS instances must run directly on the host. Veeam Backup & Replication supports physical machines and VMware vSphere VMs with pass-through RDM. Containerized deployments are not supported.
* The InterSystems IRIS data volumes must reside on a storage system that is compatible with the Universal Storage API and registered in Veeam Backup & Replication with the Block storage for application protection role. For details, see [Storage System Registration](iris_storage_registration.md).
* At least one Linux-based backup proxy must be available. Veeam Backup & Replication uses Linux-based proxies to mount the storage snapshots and read the data with the unstructured backup engine.
* Veeam Backup & Replication interacts with the storage system only over the Universal Storage API and never communicates with the storage system directly.
* Before you restore an IRIS instance from a storage snapshot, create an auxiliary host for the LUN mount in the storage-system interface. Do not use the vim aux prefix in its name: Veeam Backup & Replication reserves this prefix for hosts that it creates automatically and removes when the storage system is removed from the Veeam Backup & Replication infrastructure.
* The policy does not process the IRIS journal (log) files, so point-in-time restore is not available. For details, see [Backup Types](iris_backup_types.md).

Page updated 2026-07-24

