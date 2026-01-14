---
title: "How Mounting Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veo_mount.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# How Mounting Works

In this article

To facilitate data transfer, Veeam Explorer for Oracle uses mounting operations during data recovery.

Mounting is performed by the Veeam Mount Service component which is deployed on the mount server associated with the backup repository. For more information, see [Mount Servers](mount_server.md).

During mounting, the Veeam Mount Service retrieves a file system from the backup repository, attaches it to the hard drive of the target machine and creates a mount point. Where the file system is mounted to depends on the recovery operation.

* For restore, publishing and instant recovery, mounting is performed from the backup repository to the target server.
* For export as RMAN backup and export of database files for Linux machines, mounting is performed from the backup repository to the staging server.
* For export of database files for Windows machines, mounting is performed from the backup repository to the machine where Veeam Explorer for Oracle is opened.

Note that when restoring your data as of the state prior to a specific transaction, Veeam Explorer for Oracle requires an additional mount point to be created to display a list of available transactions in the recovery wizard. In this case, the Veeam Mount Service also mounts the necessary file system from the backup repository to the staging server. The Veeam Oracle Restore Service deployed on the staging server (for Windows machines) or Veeam Explorer for Oracle itself (for Linux machines) obtains a list of available transactions, which Veeam Explorer for Oracle displays in the recovery wizard. For more information, see [Configuring Staging Oracle Server](veor_staging_server.md).

The underlying technology used for mounting depends on the operating system of the Oracle machine.

* To mount a file system to machines with Microsoft Windows, the Veeam Mount Service uses the iSCSI protocol. The target machine or the staging server acts as an iSCSI initiator, and the mount server associated with the backup repository acts as an iSCSI target. The iSCSI mount point is non-persistent and only exists during the recovery process.
* To mount a file system to machines with Linux, the Veeam Mount Service uses [FUSE](https://www.kernel.org/doc/html/latest/filesystems/fuse.html).

Page updated 10/6/2025

Page content applies to build 13.0.1.1071
