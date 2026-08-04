---
title: "How Publishing Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_how_publishing_works_web_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Publishing Works


Publishing databases with Veeam Explorer for Microsoft SQL Server works in the following manner:

1. To start the publishing process, Veeam Explorer for Microsoft SQL Server sends a restore command to the Veeam Mount Service. The service runs on the mount server associated with the backup repository.
2. The Veeam Mount Service delegates this request to the Veeam Explorers Recovery Service running on the same server.

1. The Veeam Explorers Recovery Service connects to the target server and performs a series of validations. For example, it check if the database exists on the target server.

To perform these validations and required file operations, the Veeam Explorers Recovery Service deploys persistent or runtime components on the target server and, if you publish your data up to a specific transaction, on the staging server. These components check the valid rights assignments required for database recovery, get information about the databases, and later perform the required database operations. For more information, see [Deploying Persistent and Non-Persistent Components](vesql_restore_service_web_ui.md).

The Veeam Explorers Recovery Service sends a publishing command to the Veeam Mount Service running on the mount server associated with the backup repository. The service connects to the backup repository and prepares the mounting operation.

1. The Veeam Mount Service mounts the necessary file system to the C:\VeeamFLR directory on the target Microsoft SQL Server machine. For more information, see [How Mounting Works](vesql_mount_operations_web_ui.md).

When publishing to a failover cluster, the file system is mounted to the C:\VeeamFLR directory of every node of the cluster. Note that each volume is also mounted as a separate drive, requiring a free drive letter.

The persistent or runtime components open the database from the mounted file system, so that you can perform the required operations with Microsoft SQL Server tools.

All changes to the database that occur after publishing are saved in the publishing write cache, stored on the mount server. By default, the write cache is stored in the C:\ProgramData\Veeam\Backup\IRCache\ folder of the mount server. For more information on how to configure the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).

Once the publishing operation is completed, you can export the modified database as a BAK file. For more information, see [Exporting as BAK](vesql_publish_web_ui_export.md).

After you have finished working with the published database, you can unpublish (detach) the database from the target Microsoft SQL Server machine. For more information, see [Unpublishing Databases](vesql_publish_web_ui_unpublish.md).

[![How Publishing Works](images/vesql_how_publishing_works_web_ui.webp)](images/vesql_how_publishing_works_web_ui.webp "How Publishing Works")

Page updated 2026-07-07

