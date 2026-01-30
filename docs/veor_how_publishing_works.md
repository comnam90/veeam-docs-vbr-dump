---
title: "How Publishing Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_how_publishing_works.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---

# How Publishing Works


Publishing standalone databases and Data Guard databases with Veeam Explorer for Oracle works in the following manner:

1. Veeam Explorer for Oracle connects to the Veeam Mount Service and the target server and performs a series of validations. Some aspects of the validation process vary depending on the operating system of the Oracle machine.

* For Windows machines, Veeam Explorer for Oracle deploys the Veeam Oracle Restore Service on the target server and, if you publish your data up to a specific transaction, on the staging server. This non-persistent runtime component checks the valid rights assignments required for database recovery, gets information about the databases, and later performs the required database operations. The Veeam Oracle Restore Service is removed from the target and the staging server once you unpublish the database.
* For Linux machines, Veeam Explorer for Oracle performs the necessary validations, for example, validating the SSH fingerprints of the target server, without deploying a non-persistent runtime component.

1. Veeam Explorer for Oracle sends a publishing command to the Veeam Mount Service running on the mount server associated with the backup repository. The service connects to the backup repository and prepares the mounting operation.
2. The Veeam Mount Service mounts the necessary file system to the target Oracle machine. Mounting is done to the C:\VeeamFLR directory for Windows machines or the /run/media directory for Linux machines. For more information, see [How Mounting Works](veo_mount.md).

The Veeam Oracle Restore Service (for Windows machines) or Veeam Explorer for Oracle itself (for Linux machines) opens the database from the mounted file system, so that you can perform the required operations with Oracle tools.

All changes to the database that occur after publishing are saved in the publishing write cache on the mount server.

* For Windows machines, the write cache is by default stored in the C:\ProgramData\Veeam\Backup\IRCache\ folder on the mount server. For more information on how to configure the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).
* For Linux machines, the write cache is stored in the /var/lib/veeam/IRCache folder on the target server.

Note that Data Guard databases are published as standalone Oracle databases, preserving no Data Guard infrastructure.

Once the publishing operation is completed, you can export the modified database as an Oracle RMAN backup. For more information, see [Exporting as RMAN Backup](veor_export_as_rman.md).

[![How Publishing Works](images/veor_publish.webp)](images/veor_publish.webp "How Publishing Works")


