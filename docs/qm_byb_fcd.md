---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/qm_byb_fcd.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you perform FCD Quick Migration, check the following prerequisites and limitations.

* All FCDs that you plan to migrate, must be located on a vPower NFS datastore that is mounted to the target cluster.
* If redo logs are stored on a custom datastore, Veeam Backup & Replication checks that these redo logs are available on this datastore.

* The target datastore to which you want to migrate FCDs must meet the following requirements:

* The datastore must be added to the infrastructure of the vCenter which you specified to perform FCD Quick Migration.
* The datastore must be mounted to all ESXi hosts of a cluster which you have selected to perform FCD Quick Migration.
* The datastore must have enough free space for all migrated FDCs.
* You can not migrate FCDs to the vPower NFS datastore.
* You must use a datastore other than the [one selected for storing redo logs](instant_fcd_recovery_write_cache.md).

* You can not migrate FCDs to the same datastore where they have already been registered.


