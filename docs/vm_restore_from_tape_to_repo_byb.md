---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_restore_from_tape_to_repo_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you start restoring backups from tape to repository, consider the following:

* [Item restore](https://helpcenter.veeam.com/docs/vbr/em/em_backup_restore_app_items.html) in the Enterprise Manager from backups restored from tapes to the repository is not supported.
* Within one restore session, you can select either VMs and physical machines, or Veeam Plug-In database servers. You cannot combine restoring Veeam Plug-In backup files with other types of backups.
* When restoring Veeam Plug-In backups, only the Backup repository option is available at the Destination step of the wizard. You can restore Veeam Plug-In backups only to backup repositories added to the backup infrastructure.
* The backup chain consistency for Veeam Plug-In backups cannot be verified until the backup files have been restored from tape.
* Restoring machine backups from tapes to object storage repositories is not supported.
* [For backup to tape jobs from the HPE StoreOnce appliance] Restoring backups from tapes to a different HPE StoreOnce appliance is not supported if the source HPE StoreOnce appliance uses the variable block size and the target HPE StoreOnce appliance uses the fixed block size.

Page updated 2026-07-22

