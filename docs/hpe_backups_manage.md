---
title: "Managing Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_backups_manage.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Managing Backups


Veeam Backup & Replication stores information on all protected VMs in the configuration database. Even if a VM is no longer protected by any configured backup job and even if the VM no longer exists in the HPE Morpheus VM Essentials environment, records about created backups will not be deleted from the database until Veeam Backup & Replication automatically removes all restore points associated with this VM according to the retention settings saved in the backup metadata. You can manage VM backups as long as their records are present in the configuration database.

In This Section

* [Viewing Backup Properties](hpe_backups_view_properties.md)
* [Verifying Backups](hpe_backups_verify.md)
* [Exporting Backups](hpe_backups_export.md)
* [Copying Backups](hpe_backups_copy.md)
* [Copying Backups to Tapes](hpe_backups_copy_tape.md)
* [Deleting Backups](hpe_backups_delete.md)


