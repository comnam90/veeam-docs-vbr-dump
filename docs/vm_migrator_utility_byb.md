---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_utility_byb.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before using Veeam VM Migrator, consider the following:

* You must create a [configuration backup](export_vbr_config.md) of Veeam Backup & Replication database before using Veeam VM Migrator.
* Do not run backup jobs for VMs from the new vCenter until you finish working with Veeam VM Migrator. Otherwise, if there are any VMs backed up from the new vCenter, it will not be possible to migrate these VMs because new VM objects will already exist in the database.

* If you use the replication feature:

+ Veeam VM Migrator supports source vCenter migration only. If replication target vCenter is changed, you will need to manually map source VMs to their replicas.
+ Replica VMs must be mapped manually using the replica mapping feature in  Veeam Backup & Replication console.

For more information on replica mapping, see [Replica Seeding and Mapping](replica_seeding.md).

* Virtual labs should be [recreated](create_vlab.md) manually after migration.
* The VM containers will not be updated, you will need to manually re-add all folders, tags, datastores, clusters and resource pools in the list of VMs in backup and/or replica job settings.
* You can not resolve MORef-ID misalignment for jobs that target a Cloud Connect repository.


