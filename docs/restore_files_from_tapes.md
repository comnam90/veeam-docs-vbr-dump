---
title: "Restoring Files from Tape"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_files_from_tapes.html"
last_updated: "6/14/2024"
product_version: "13.0.1.1071"
---

# Restoring Files from Tape


To restore files or NDMP volumes backed up to tape, use the Restore from Tape wizard.

If the tapes are online in your tape device, Veeam Backup & Replication will get the needed data automatically. If the tapes are offline, Veeam Backup & Replication will list the names of the required tapes.

|  |
| --- |
| Note |
| The Files from Tape Restore wizard allows you to restore files and folders archived to tape. You cannot restore VM guest OS files using this wizard. To restore VM guest OS files, restore a machine backup from tape to a backup repository and perform VM guest OS files restore. For more information, see [Backup Restore from Tape to Repository](vm_restore_from_tape_to_repository.md). |

Restoring Entire Tapes

For information about restoring entire tapes, see [Restoring Entire Tapes](restoring_entire_tapes.md).

This section will guide you through all steps of the wizard and provide explanation on available options for restoring files from tapes and for restoring entire tapes.

To restore files from tape or to restore entire tapes, follow the next steps:

1. [Launch the Restore from Tape wizard](restore_files_from_tape_launch.md).
2. [Choose files to restore](restore_files_from_tape_objects.md).
3. [Specify restore destination](restore_files_from_tape_target.md).
4. [Specify restore options](restore_files_from_tape_options.md).
5. [Finish working with the wizard](restore_files_from_tape_review.md).


