---
title: "Backup of VMs on Microsoft SMB3"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hv_smb3_intro.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Backup of VMs on Microsoft SMB3

In this article

Microsoft Hyper-V provides the ability to store VM files on SMB3 file shares. Veeam Backup & Replication works with both standalone and clustered SMB3 servers. It supports VMs whose VM disks are located on SMB3 shares and allows you to perform backup, replication and file copy operations for such VMs without taking VMs offline.

For backup of VMs registered on Microsoft Hyper-V Server 2016 and later versions, Veeam Backup & Replication uses a mechanism based on production checkpoints. For more information, see [Online Backup](online_backup.md#2016).

If you plan to process VMs whose disks reside on SMB3 shared folders registered on Microsoft Hyper-V Server 2016 or later, you do not need to add the SMB3 server to the backup infrastructure. However, if you do not add the SMB3 server, you cannot specify the Max snapshots and latency control settings for SMB3 shared folders.

The above applies to SMB3 shares running on Microsoft Windows or any other non-Windows based SMB3 source.

For more information, see [Adding Microsoft SMB3 Servers](smb.md).

Related Topics

* [Online Backup](online_backup.md)
* [Adding Microsoft SMB3 Servers](smb.md)

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
