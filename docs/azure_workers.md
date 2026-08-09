---
title: "Managing Worker Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_workers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Worker Instances


To perform most data protection and disaster recovery operations (such as creating backups in repositories and restoring backed-up data), the backup appliance uses worker instances. A worker instance is an auxiliary Linux-based virtual machine that is responsible for the interaction between the backup appliance and other solution architecture components. Worker instances process backup workload and distribute backup traffic when transferring data to repositories.

Each worker instance is launched in a specific Azure region and keeps running for the duration of the backup or restore process. For more information on regions in which the backup appliance launches worker instances, see [Worker Instances](azure_worker_instances.md).

|  |
| --- |
| Note |
| You can tell worker instances from other Azure VMs running in your environment — all worker instances launched by the backup appliance will have the wordVBA in their names, and the Veeam backup appliance ID tag. To learn how to assign custom tags to worker instances, see [Adding Worker Instance Tags](azure_worker_instance_tags.md). |

In This Section

* [Managing Worker Configurations](azure_worker_configurations.md)
* [Managing Worker Profiles](azure_worker_profiles.md)
* [Adding Tags to Worker Instances](azure_worker_instance_tags.md)
* [Removing Worker Instances](azure_worker_instance_remove.md)

Page updated 2026-07-01

