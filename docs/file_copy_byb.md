---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_copy_byb.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you configure a file copy job, check the following prerequisites:

Backup infrastructure components that will take part in the file copying process must be added to the backup infrastructure and properly configured. These include a source and target host or server between which files and folders will be copied.

Consider the following limitations:

* File copy is not supported for Unix systems, for example, Solaris, FreeBSD and AIX.
* Veeam Backup & Replication does not preserve the Access Control List (ACL) settings for copied guest OS folders. The ACL settings are preserved for files only.

|  |
| --- |
| Tip |
| You can restore the ACL settings for recovered guest OS files and folders using [Guest OS File Restore](guest_file_recovery.md). |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
