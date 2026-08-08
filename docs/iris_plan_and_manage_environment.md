---
title: "Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_plan_and_manage_environment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Environment Planning


Before you deploy Veeam components and start protecting InterSystems IRIS instances, keep in mind the following requirements and limitations:

* InterSystems IRIS instances must run directly on the host. Veeam Backup & Replication supports physical machines and VMware vSphere VMs with pass-through RDM. Containerized deployments are not supported.
* The InterSystems IRIS data volumes must reside on a storage system that is compatible with the Universal Storage API and registered in Veeam Backup & Replication with the Block storage for application protection role. For details, see [Registering Storage System for Application Protection](iris_storage_registration.md).
* If you plan to run the policy in backup mode, at least one Linux-based backup proxy must be available. Veeam Backup & Replication uses Linux-based proxies to mount the storage snapshots and read the data with the unstructured data backup engine. Backup proxies are not used in snapshot-only mode.
* Veeam Backup & Replication interacts with the storage system only over the Universal Storage API and never communicates with the storage system directly.
* Before you restore an InterSystems IRIS instance from a storage snapshot, create an auxiliary host for the LUN mount in the storage system interface. Do not use the VeeamAUX prefix in the name because Veeam Backup & Replication reserves this prefix for hosts that it creates automatically, and removes when the storage system is removed from the Veeam Backup & Replication infrastructure.
* The policy does not process the InterSystems IRIS journal (log) files, so point-in-time restore is not available. For details, see [Backup Types](iris_backup_types.md).

Page updated 2026-08-06

