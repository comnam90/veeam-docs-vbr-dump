---
title: "File Restore from Tape"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_restore_from_tape.html"
last_updated: "5/27/2024"
product_version: "13.0.1.1071"
---

# File Restore from Tape

In this article

You can restore data previously archived with file to tape jobs and with backup to tape jobs where the sources are unstructured data backup jobs or repositories that store unstructured data backups. You can restore the following data:

* Microsoft Windows files and folders.
* Linux files and folders.

* Files and folders on SMB (CIFS) and NFS file shares.
* NDMP volumes.
* Content of entire tapes.

The file restore process allows you to restore files to any restore point available on tape.

Limitations for NFS File Share Restore

If you restore files to the NFS file share running the NFS protocol version different from the NFS version of the source file share, Veeam Backup & Replication does not restore security attributes.

Limitations for NDMP Volumes Restore

* Only restore of whole volume is supported.
* Only restore to original location or to a similar NDMP server is supported.

Related Topics

* [How Restoring Files from Tape Works](tape_restoring_files_from_tape.md)
* [Before You Begin](file_from_tape_before_you_begin.md)
* [Restoring Files from Tape](restore_files_from_tapes.md)

Page updated 5/27/2024

Page content applies to build 13.0.1.1071
