---
title: "Copying Tapes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/copying_tapes.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---

# Copying Tapes


You can use the tape copy feature to migrate backups or files stored on previous generation tapes to newer ones.

You can also use this feature to make copies of tapes.

Before starting a tape copy job, check the following prerequisites:

* The tape server must have at least 1 GB of RAM per each tape drive used during a tape copy session.
* The tapes to copy must not be occupied by any other operations, such as backup, restore, cataloging. During the tape copy procedure, the tapes will be locked.
* The tapes to copy must be cataloged. Tapes in the Unrecognized media pool are not available for copying. For more information, see [Cataloging Tapes](cataloging_tapes.md).
* All tapes to copy and machine backups on them must be decrypted. Encrypted tapes cannot be copied. Encrypted backups are skipped from copying. For more information on how to decrypt backup files and tapes, see [Decrypting Backups](decrypt_with_pass.md) and [Restoring Data from Encrypted Tapes](tapes_restore_encrypted.md).
* The source and target tape libraries must have at least one free tape drive each. If the tape copying is performed within one tape library, it must have at least two free drives.

|  |
| --- |
| Note |
| Due to hardware peculiarities, the speed of copying tapes is on average 15% lower than the speed of writing backups to tapes from the backup repository. |

To copy content of a tape to another one, use the Copy Tapes wizard.

1. [Launch the Copy Tapes wizard](tape_copy_launch.md).
2. [Choose source tapes to copy](tape_copy_source.md).
3. [Choose a target media pool where to copy the tapes](tape_copy_target.md).
4. [Specify tape copy options](tape_copy_options.md).
5. [Finish working with the wizard](tape_copy_finish.md).


