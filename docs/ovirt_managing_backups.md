---
title: "Managing Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_managing_backups.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# Managing Backups


Veeam Plug-in for oVirt KVM stores information on all protected VMs in the configuration database. Even if a VM is no longer protected by any configured backup job and even if the VM no longer exists in the oVirt KVM environment, records about created backups will not be deleted from the database until Veeam Plug-in for oVirt KVM automatically removes all restore points associated with this VM according to the retention settings saved in the backup metadata. You can manage VM backups as long as their records are present in the configuration database.

In This Section

* [Viewing Backup Properties](ovirt_view_backup_properties.md)
* [Verifying Backups](ovirt_verify_backups.md)
* [Exporting Backups](ovirt_export_backups.md)
* [Copying Backups](ovirt_backup_copy_job.md)
* [Copying Backups to Tapes](ovirt_backup_tape_jobs.md)
* [Deleting Backups](ovirt_retention.md)


