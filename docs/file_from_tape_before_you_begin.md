---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_from_tape_before_you_begin.html"
last_updated: "6/14/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you start the file restore from tape, consider the following:

* If the tape backup contains a large quantity of files, for example, more than 1 000 000 files in 1 000 folders, you must provide the following system resources for restore: backup server — 2.6 GB RAM per each 1 000 000 files.
* If a job is unable to complete within 21 days period, it will be stopped with the Failed status.

* Restore to the original location is not supported for backups to tape from NAS filers (NetApp Data ONTAP, Lenovo ThinkSystem DM/DG Series, Dell PowerScale or Nutanix Files Storage).

* Veeam Backup & Replication does not support restore of symbolic links backed up on one file system type to a different file system type. For example, you cannot backup files and folders with symbolic links on a Windows system and restore them to a Linux system.


