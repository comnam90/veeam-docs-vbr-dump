---
title: "How Mounting Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_mount_operations.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# How Mounting Works


To facilitate data transfer, Veeam Explorer for Microsoft SQL Server uses mounting operations during data recovery.

Mounting is performed by the Veeam Mount Service component which is deployed on the mount server associated with the backup repository. For more information, see [Mount Servers](mount_server.md).

During mounting, the Veeam Mount Service retrieves a file system from the backup repository, attaches it to the hard drive of the target machine and creates a mount point. For restore, publishing and instant recovery, mounting is performed from the backup repository to the target server, and in the case of export — from the backup repository to the staging server.

Note that when restoring your data to a specific transaction and when restoring database schema and data, Veeam Explorer for Microsoft SQL Server requires an additional mount point to be created to display a list of available transactions or database objects in the recovery wizard. In these cases, the Veeam Mount Service also mounts the necessary file system from the backup repository to the staging server. The persistent or runtime components deployed on the staging server obtain a list of the available transactions or database objects, which Veeam Explorer for Microsoft SQL Server displays in the recovery wizard. For more information, see [Configuring Staging SQL Server](vesql_configure_staging.md).

To mount a file system, the Veeam Mount Service uses the iSCSI protocol. The target machine or the staging Microsoft SQL Server acts as an iSCSI initiator, and the mount server associated with the backup repository acts as an iSCSI target. The iSCSI mount point is non-persistent and only exists during the recovery process.


