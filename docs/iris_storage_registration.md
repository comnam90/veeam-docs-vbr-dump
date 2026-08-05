---
title: "Registering Storage System for Application Protection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_storage_registration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Registering Storage System for Application Protection


To enable InterSystems IRIS application backup policies to use storage snapshots, the storage system that hosts the InterSystems IRIS instance data volumes must be registered in Veeam Backup & Replication with the Block storage for application protection role. This role enables Veeam Backup & Replication to create and manage storage snapshots and thin clones through the Universal Storage API for application-consistent backup and restore. Without this role, IRIS backup policies cannot process storage snapshots on the registered storage system.

The storage system must be compatible with the Universal Storage API. Veeam Backup & Replication interacts with the storage system only over the Universal Storage API and never communicates with it directly. To learn how to operate with Universal Storage API integrated systems in Veeam Backup & Replication, see [Universal Storage API Integrated Systems](universal_storage_integration_api.md).

Page updated 2026-07-28

