---
title: "Preparing for File Browsing and Searching"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/preparing_for_file_browsing.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Preparing for File Browsing and Searching


If you have Veeam Backup & Replication and Veeam Backup Enterprise Manager installed, you can use indexing capabilities to quickly find necessary files and folders.

To use guest file system indexing:

1. Enable guest file system indexing on the Guest Processing step of the backup job wizard. For more information, see [Configure Guest Processing Settings](jobs_edit_guest_settings.md).
2. Run the backup job with guest file system indexing enabled.
3. Perform catalog replication. For more information, see [Performing Catalog Replication and Indexing](performing_catalog_replication.md).

Alternatively, you can process the machine without guest file system indexing. Indexing may be disabled at the time of restore point creation, or indexing operation may fail. In this case, the restore point of a Windows machine is mounted to the backup server that manages the job, and the restore point of a non-Windows machine is mounted to a helper host or helper appliance.

Then you will be able to locate necessary files and folders and perform restore operation. For more information, see [Browsing Machine Backups for Guest OS Files](browsing_vm_backups.md).

In This Section

* [Performing Catalog Replication and Indexing](performing_catalog_replication.md)
* [Preparing for File Search and Restore (non-Windows machines)](em_preparing_for_linux_guest_file.md)


