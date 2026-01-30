---
title: "How Mounting Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_mount.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# How Mounting Works


To facilitate data transfer, Veeam Explorer for PostgreSQL uses mounting operations during data recovery.

Mounting is performed by the Veeam Mount Service component which is deployed on the mount server associated with the backup repository. For more information, see [Mount Servers](mount_server.md). To mount a file system to the target machine, the Veeam Mount Service uses [FUSE](https://www.kernel.org/doc/html/latest/filesystems/fuse.html).

During mounting, the Veeam Mount Service retrieves a file system from the backup repository, attaches it to the hard drive of the target machine and creates a mount point. For restore, publishing and instant recovery, mounting is performed from the backup repository to the target server, and in the case of export, from the backup repository to the staging server.


