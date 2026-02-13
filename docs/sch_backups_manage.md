---
title: "Managing Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backups_manage.html"
last_updated: "9/6/2024"
product_version: "13.0.1.1071"
---

# Managing Backups


Veeam Plug-in for Scale Computing HyperCore stores information on all protected Scale Computing HyperCore VMs in the configuration database. Even if a VM is no longer protected by any configured backup job and even if the VM no longer exists in the Scale Computing HyperCore environment, records about created backups will not be deleted from the database until Veeam Plug-in for Scale Computing HyperCore automatically removes all restore points associated with this VM according to the retention settings saved in the backup metadata. You can manage Scale Computing HyperCore VM backups as long as their records are present in the configuration database.

In This Section

* [Viewing Backup Properties](sch_backups_view_properties.md)
* [Verifying Backups](sch_backups_verify.md)
* [Exporting Backups](sch_backups_export.md)
* [Copying Backups](sch_backups_copy.md)
* [Copying Backups to Tapes](sch_backups_copy_tape.md)
* [Deleting Backups](sch_backups_delete.md)


