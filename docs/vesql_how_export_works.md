---
title: "How Export Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_how_export_works.html"
last_updated: "2/9/2026"
product_version: "13.0.1.1071"
---

# How Export Works


Veeam Explorer for Microsoft SQL Server allows you to export databases to the machine where Veeam Explorer for Microsoft SQL Server is opened. You can export your database as database files (MDF and LDF files) or as a BAK file.

Exporting databases with Veeam Explorer for Microsoft SQL Server works in the following manner:

1. Veeam Explorer for Microsoft SQL Server connects to the Veeam Mount Service and the staging server and performs a series of validations. For example, it checks if the staging server has enough free space for the staged data.

Veeam Explorer for Microsoft SQL Server deploys persistent or runtime components on the staging server, which check the valid rights assignments required for export, get information about the databases, and later perform required file operations. For more information on how these components are deployed, see [Deploying Persistent and Non-Persistent Components](vesql_restore_service.md).

1. Veeam Explorer for Microsoft SQL Server sends an export command to the Veeam Mount Service running on the mount server associated with the backup repository. The service connects to the backup repository and prepares the mounting operation.
2. The Veeam Mount Service mounts the necessary file system to the C:\VeeamFLR directory on the staging Microsoft SQL Server machine. For more information, see [How Mounting Works](vesql_mount_operations.md).
3. The persistent or runtime components save data from the mounted file system to the C:\Windows\TEMP directory on the staging Microsoft SQL Server machine. This step helps convert the data into the necessary format before data transfer.
4. The persistent or runtime components send the staged data to the machine where Veeam Explorer for Microsoft SQL Server is opened. Data transfer is established by data movers running on the staging server and the target machine.

After the export operation successfully completes, Veeam Explorer for Microsoft SQL Server unmounts the mounted file system and removes the staged data from the staging server.

![How Export Works](images/vesql_export.webp "How Export Works")


