---
title: "Item Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/item_recovery_hv.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Item Recovery


Item recovery includes the following methods for the Microsoft Hyper-V platform:

* [VM files restore](vmfile_recovery.md) — to restore VM files (.XML, .VMCX and so on) without restoring the entire VM.

Veeam Backup & Replication provides the following platform-independent methods for item recovery:

* [Guest OS file restore](guest_file_recovery.md) — to restore individual guest OS files from Windows, Linux, Mac and other guest OS file systems. You can restore files and folders directly from a regular image-level backup, storage snapshot or replica.
* [Application items restore](restore_veeam_explorers.md) — to restore items from different applications such as Microsoft Active Directory, Microsoft SQL Server and so on. Application items are recovered directly from VM backups and replicas. To recover application items, Veeam Backup & Replication uses the capabilities of Veeam Explorers.


