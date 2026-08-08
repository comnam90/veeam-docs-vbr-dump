---
title: "Backup Restore from Tape to Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_restore_from_tape_to_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Restore from Tape to Repository


This option allows you to copy VM and database server backups from tape to a staging repository:

* For VM backups, this recovery scenario can be used if you need some backups on disk for later use or for the guest OS files restore. You can restore full backups or incremental backups to a repository or any location of your choice.
* For Veeam Plug-In backups, restoring backups from tape to a backup repository is the first step in the database recovery process. Once the backups are copied from tape to a backup repository, you can continue the database recovery operation.

For both VM and database server backups, the restored backup is registered in the Veeam Backup & Replication console as an imported disk backup so that you can use it for any restore from disk scenario later on. For one restore session at a time, you can choose one restore point available on tape.

To restore data from [backup to tape jobs for unstructured data backups](btt_nas.md), use the file restore from tape functionality. For more information, see [File Restore from Tape](file_restore_from_tape.md).

Related Topics

* [How Restoring Backups from Tape to Repository Works](restoring_vm_from_tape_to_repository.md)
* [Restoring Backups from Tape to Repository](restoring_backups_from_tape.md)
* [Guest OS File Restore](guest_file_recovery.md)

Page updated 2026-07-22

