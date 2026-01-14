---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_hpe_storeonce_byb.html"
last_updated: "10/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a backup copy job for HPE StoreOnce backup repository, check the following requirements:

* The minimum supported software versions of are the following:

* For the third generation, the minimum version is 3.18.18.
* For the fourth generation, the minimum version is 4.2.3.

* Make sure that all backup infrastructure components that take part in the backup copy process are added to the backup infrastructure. These components include the source and target repositories between which data is copied. For more information on how to add a backup repository, see [Backup Repositories](backup_repository.md).
* To perform the health check for backup files, you must use HPE StoreOnce version 5.2 or later.
* Veeam Backup & Replication does not perform the health check for encrypted and compressed backup files.
* Check that repositories between which you plan to copy data have a direct connection to each other. This is required because Veeam Backup & Replication uses the HPE StoreOnce Catalyst Copy technology to copy backup files.

This direct connection must be of the same type as the connection that [you select when adding](dsa_repository_server.md) the target HPE StoreOnce. For example, if you connected the target HPE StoreOnce repository over Fibre Channel, you must connect the source HPE StoreOnce to the target HPE StoreOnce over Fibre Channel.

* HPE StoreOnce repositories connected over Fibre Channel require the two-way connection. Zone the source initiator World Wide Names (WWNs) with the destination target WWNs, and zone the destination initiator WWNs with the source target WWNs.
* If source backup repository has backup immutability disabled while the target repository is immutable, backup copy job will work in non-immutable mode.
* If source and target HPE StoreOnce backup repositories are configured with different block chunking algorithm, backup copy job will copy the data without changing the block sizes.
* If source backup job has [GFS retention policy](gfs_retention_policy.md) configured, its GFS immutability settings will be applied to the backup files copied to the target HPE StoreOnce backup repository.
* If you plan to use pre-job and post-job scripts, you must create scripts before you configure the backup copy job.

* [For Linux-based backup server] The following applies to pre-job and post-job scripts:

* Bash scripts must use Linux-style line ednings (LF).
* Only the .SH and .PS1 file extensions are supported.

* Scripts with the .EXE file extension are not supported.
* Script impersonation is not supported.

To upload scripts to the Linux backup server, in the Veeam Backup & Replication console, navigate to the Files node. Then, copy script files to the /var/lib/veeam/scripts folder on the Linux backup server.

Page updated 10/21/2025

Page content applies to build 13.0.1.1071
