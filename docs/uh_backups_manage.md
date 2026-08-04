---
title: "Managing Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_backups_manage.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Backups


Veeam Backup & Replication stores information on all protected VMs in the configuration database. Even if a VM is no longer protected by any configured backup job and even if the VM no longer exists in the universal hypervisor environment, records about created backups will not be deleted from the database until Veeam Backup & Replication automatically removes all restore points associated with this VM according to the retention settings saved in the backup metadata. You can manage VM backups as long as their records are present in the configuration database.

In This Section

* [Viewing Backup Properties](uh_backups_view_properties.md)
* [Verifying Backups](uh_backups_verify.md)
* [Exporting Backups](uh_backups_export.md)
* [Copying Backups](uh_backups_copy.md)
* [Copying Backups to Tapes](uh_backups_copy_tape.md)
* [Deleting Backups](uh_backups_delete.md)

Page updated 2026-02-24

