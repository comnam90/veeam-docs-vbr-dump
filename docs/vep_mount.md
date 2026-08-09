---
title: "How Mounting Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_mount.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Mounting Works


To facilitate data transfer, Veeam Explorer for PostgreSQL uses mounting operations during data recovery.

Mounting is performed by the Veeam Mount Service component which is deployed on the mount server associated with the backup repository. For more information, see [Mount Servers](mount_server.md).

During mounting, the Veeam Mount Service retrieves a file system from the backup repository, attaches it to the hard drive of the target machine and creates a mount point. For restore, publishing and instant recovery, mounting is performed from the backup repository to the target server, and in the case of export, from the backup repository to the staging server.

The underlying technology used for mounting depends on the operating system of the PostgreSQL machine.

* To mount a file system to machines with Microsoft Windows, the Veeam Mount Service uses the iSCSI protocol. The target machine or the staging server acts as an iSCSI initiator, and the mount server associated with the backup repository acts as an iSCSI target. The iSCSI mount point is non-persistent and only exists during the recovery process.
* To mount a file system to machines with Linux, the Veeam Mount Service uses [FUSE](https://www.kernel.org/doc/html/latest/filesystems/fuse/index.html).

Page updated 2026-07-17

