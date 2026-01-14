---
title: "Veeam VM Migrator"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/veeam_vm_migrator.html"
last_updated: "10/28/2025"
product_version: "13.0.1.1071"
---

# Veeam VM Migrator

In this article

Veeam VM Migrator cmdlets set resolves MORef ID misalignment after VMware vCenter migration, preventing VMs with changed MORef IDs from being treated as new VMs. It allows jobs to continue the incremental processing of these VMs.

Considerations and Limitations

Before using Veeam VM Migrator, consider the following:

* You must make a configuration backup of Veeam Backup & Replication database before using Veeam VM Migrator.
* Do not run backup jobs for VMs from the new vCenter until you finish working with Veeam VM Migrator. Otherwise, if there are any VMs backed up from the new vCenter, it will not be possible to migrate these VMs because the new VM objects will already exist in the database.
* Old vCenter must not be used by Veeam Backup & Replication after migration.

* If you use the replication feature:

+ Veeam VM Migrator supports a source vCenter migration only. If replication target vCenter is changed, you will need to manually map source VMs to their replicas.
+ Replica VMs must be mapped manually using the replica mapping feature in  Veeam Backup & Replication console.

* Virtual labs should be recreated manually after migration.
* The VM containers will not be updated, you will need to manually re-add all folders, tags, datastores, clusters and resource pools in the list of VMs in backup and/or replica job settings.

In This Section

| Cmdlet | Operation |
| --- | --- |
| [Set-VBRVmBiosUuid](set-vbrvmbiosuuid.md) | Collects MORef IDs. |
| [Set-VBRVCenterName](set-vbrvcentername.md) | Modifies VMware vCenter name. |
| [Generate-VBRViMigrationSpecificationFile](generate-vbrvimigrationspecificationfile.md) | Generates a migration task file. |
| [Start-VBRViVMMigration](start-vbrvivmmigration.md) | Starts the MORef ID update. |

Page updated 10/28/2025

Page content applies to build 13.0.1.1071
