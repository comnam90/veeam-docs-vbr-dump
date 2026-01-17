---
title: "Windows Server"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_prepare_physical_windows.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Windows Server


Preparing Backup

You can restore files from a backup of a physical Windows server created with or without indexing.

To prepare a backup with guest file indexing:

1. Enable guest file system indexing on the Guest Processing step of the backup job wizard.
2. Run the backup job with guest file system indexing enabled.
3. Make sure the indexing data is imported to the Veeam backup database, and catalog replication is completed successfully. For details, see the [Performing Catalog Replication and Indexing](performing_catalog_replication.md) section.

If you restore files from an indexed guest OS, you do not need to mount the restore point for browsing purposes — file hierarchy is presented using the index. The restore point will be only mounted once (during 1-Click file restore process itself) — to the mount server associated with backup repository where Veeam Agent backups are stored.

Alternatively, you can process the backups created without guest file system indexing — for example, if indexing was disabled at restore point creation time, or if indexing operation failed. For such a server, its selected restore point first will be mounted (for the browsing and search purposes) to the Veeam backup server integrated with Veeam Agent. After you locate the necessary file and initiates 1-Click file restore, the restore point will be mounted to the mount server associated with the repository.

Other Prerequisites

During guest file restore to the original location, you are prompted for the credentials to access the target Windows server. Enter a user name and password; make sure that the account has sufficient access rights.


