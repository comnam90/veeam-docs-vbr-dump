---
title: "Adding Microsoft SMB3 Servers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/smb.html"
last_updated: "2/6/2025"
product_version: "13.0.1.1071"
---

# Adding Microsoft SMB3 Servers


Veeam Backup & Replication supports Microsoft Hyper-V VMs whose disks reside on Microsoft SMB3 file shares and lets you perform backup, replication and file copy operations for such VMs.

To work with VMs residing on Microsoft SMB3 shared folders, you must add to the backup infrastructure the following components:

* Microsoft Hyper-V host on which VMs are registered.
* Microsoft SMB3 server or cluster hosting shared folders with VM disks.

If you do not add a Microsoft SMB3 server or cluster to the backup infrastructure, or if the SMB3 server host has several assigned roles (for example, if the host is a Hyper-V server and an SMB3 server for another Hyper-V host), Veeam Backup & Replication will not be able to use the changed block tracking mechanism and latency control (I/O control) to process such VMs.

|  |
| --- |
| Note |
| If VMs whose disks reside on SMB3 shared folders are registered on Microsoft Hyper-V Server 2016 or later, adding a Microsoft SMB3 server is not required. Note, however, that if you do not add the Microsoft SMB3 server, you will not be able to specify the Max snapshots and latency control settings for SMB3 shared folders. |

Before you add a Microsoft SMB3 server or cluster, [check prerequisites](smb_before_you_begin.md). Then use the New SMB3 Server wizard to add the server or cluster.

1. [Launch the New SMB3 Server wizard](launch_the_new_smb_v3_server.md).
2. [Specify a server name and address](smb_name.md).
3. [Specify a server type](smb_type.md).
4. [Specify credentials](smb_credentials.md).
5. [Review components](smb_apply.md).
6. [Finish working with the wizard](smb_summary.md).
7. [Configure SMB3 shares](smb_configure.md).


