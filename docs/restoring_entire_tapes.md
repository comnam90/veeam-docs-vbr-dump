---
title: "Restoring Entire Tapes"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restoring_entire_tapes.html"
last_updated: "8/25/2023"
product_version: "13.0.1.1071"
---

# Restoring Entire Tapes

In this article

A special case of file restore from tape described in section [Restoring Files from Tape](restore_files_from_tapes.md) is restoring content of entire tapes. That can be useful in various situations. For example:

* If a media set is damaged, you can use the entire tape restore to recover all available data stored on tapes in this media set.
* You want to check what content is stored on a particular tape.
* Audit requires checking the content of the tapes.

Before restoring tapes, consider the following:

* Restore of the content of entire tapes can be performed to a non-original location only.
* NDMP data is skipped from restore.
* The tapes to restore must be online.
* The tapes to restore must be cataloged. Tapes in the Unrecognized media pool are not available for restore. For more information, see [Cataloging Tapes](cataloging_tapes.md).
* Backup files on tapes to restore must be decrypted. Encrypted backup files are skipped from restore. For more information, see [Add Optional Media Pool Settings](add_media_pool_encryption.md).
* When restoring entire tapes, Veeam Backup & Replication creates a separate folder for each host whose files are backed up on the tapes.
* The entire restore tape job preserves the folder structure and restores all file and folder versions as is. If the tape stores several file versions of the same file or folder, older versions get date postfixes in the names.
* If some files on the tapes to restore have dependent file parts on other tapes, Veeam Backup & Replication will require these tapes to restore the full content of the selected tapes in the consistent manner.
* If you are restoring data from tapes that were previously copied, as described in section [Copying Tapes](copying_tapes.md), Veeam Backup & Replication will use the most recent online copy as a source for restore.

For information on how to restore entire tapes, see [Restoring Files from Tape](restore_files_from_tapes.md).

Page updated 8/25/2023

Page content applies to build 13.0.1.1071
