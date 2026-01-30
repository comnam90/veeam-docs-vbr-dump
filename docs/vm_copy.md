---
title: "VM Copy for VMware vSphere"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_copy.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# VM Copy for VMware vSphere


With Veeam Backup & Replication, you can run a VM copy job to create an independent fully-functioning copy of a VM or VM container (host, cluster, folder, resource pool, VirtualApp, datastore or tag) on the selected storage. VM copying can be helpful if you want to move your datacenter, create a test lab and so on.

The produced copy of a VM is stored decompressed, in a native VMware vSphere format, so it can be started right away. Although VM copy is similar to replication in many respects, there are several important differences.

* VM copy is a single-use process (that is, every run of a VM copy job mirrors a VM in its latest state). Due to their nature, VM copy jobs do not support incremental runs.
* Veeam Backup & Replication does not create and maintain restore points for VM copies. If you schedule to run a VM copy job periodically, every new run will overwrite the existing copy.
* With the VM copy job, all VM disks are copied as thick, while replication allows you to preserve the format of disks or convert the disk format on the fly.

|  |
| --- |
| Note |
| When registering a VM on an ESXi host, it is registered with thin provisioned disks by default. |

* There are no failover or failback possibilities for a VM copy.

VM copy jobs use the same infrastructure components as backup jobs (for details, see [Backup Infrastructure for Backup](backup_architecture.md)). In addition to available scenarios, you can also copy VMs to a target folder on any server or host connected to the backup server.

Related Topics

[Copying VMs](copy_job.md)


