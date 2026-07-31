---
title: "Computer Discovery and Veeam Components Deployment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_discovery_and_deployment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Computer Discovery and Veeam Components Deployment


Veeam Backup & Replication supports automated deployment of Veeam components on the ODB servers that host InterSystems IRIS instances in your infrastructure.

To deploy Veeam components and discover InterSystems IRIS instances, you need to add relevant ODB servers to your Veeam Backup & Replication infrastructure. You can organize your ODB servers into one or more protection groups. Protection group settings define which servers Veeam Backup & Replication will connect to, the credentials used to connect to them, and the schedule on which discovery runs. Before you create a protection group, you must register the Universal Storage API system that hosts the IRIS data volumes in Veeam Backup & Replication with the Block storage for application protection role. To learn more about how to register a storage system in Veeam Backup & Replication, see [Universal Storage API Integrated Systems](universal_storage_integration_api.md).

For automated discovery of ODB servers and InterSystems IRIS instances, Veeam Backup & Replication uses the rescan job that runs on the backup server. To learn more, see [Rescan Job](iris_rescan_job.md).

In This Section

* [Protection Group for InterSystems IRIS Databases](iris_protection_group_hiw.md)
* [Rescan Job](iris_rescan_job.md)

Page updated 2026-07-28

