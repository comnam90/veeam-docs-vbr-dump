---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/byb_fcd.html"
last_updated: "2/13/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you perform Instant FCD Recovery, consider the following:

* The vCenter Server where the target cluster (cluster to which you plan to recover disks) is located must be version 6.7.U3 or later.
* The target cluster must be configured beforehand and added to the backup infrastructure. The hosts located in this cluster must meet the following requirements:

* ESXi hosts must be powered on.
* Veeam Backup & Replication must be able to connect to ESXi hosts.
* API version of ESXi hosts must be 6.7.U3 or later.
* ESXi must have the VMkernel network interface enabled.

* Veeam Backup & Replication does not support restore to a single ESXi host.
* You can restore a virtual disk from a backup that has at least one successfully created restore point.

* Instant FCD Recovery to VMware Cloud Director is not supported.
* The datastore [which you specify to store redirect logs](instant_fcd_recovery_write_cache.md) must meet the following requirements:

* The datastore must be added to the vCenter infrastructure and must be available for Veeam Backup & Replication to set up a connection to it.
* The datastore must be located in the same vCenter, where a cluster to which Veeam Backup & Replication will register FCDs, is located.
* The datastore must be mounted to all ESXi hosts of a cluster to which Veeam Backup & Replication will register FCDs.
* You must have at least one more additional datastore in your vCenter infrastructure, otherwise restore will fail.
* The datastore must not be the Veeam NFS datastore.

* You can assign storage policies to FCDs only if you redirect redo logs to another datastore.
* The encryption storage policies are not supported. If you select this type of policy, Veeam Backup & Replication will not be able to apply this policy to registered FCDs.

* You must have at least 10 GB of free disk space on the datastore where write cache folder is located. This disk space is required to store virtual disk updates for the restored VM.

By default, Veeam Backup & Replication writes virtual disk updates to the IRCache folder on a volume with the maximum amount of free space, for example, C:\ProgramData\Veeam\Backup\IRCache.


