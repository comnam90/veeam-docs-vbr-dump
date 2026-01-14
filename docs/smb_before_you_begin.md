---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/smb_before_you_begin.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you add a Microsoft SMB3 server or cluster to the backup infrastructure, check the following prerequisites:

* Microsoft SMB3 servers must run Microsoft Windows Server 2012 or later. Veeam Backup & Replication supports only these types of Microsoft SMB3 servers.
* Microsoft SMB3 shared folders must be properly configured. For a full list of requirements for Microsoft SMB3 shared folders, see the Requirements and supported configurations section at [Microsoft Docs](http://technet.microsoft.com/en-us/library/jj612865.aspx).
* VMs must not reside on hidden shared folders or default shared folders such as C$ or D$. When rescanning Microsoft SMB3 file shared folders, Veeam Backup & Replication skips these types of folders.
* [For Veeam Cloud Connect Replication scenario] You cannot use Microsoft SMB3 shared folder as a storage for VM replicas.
* To read/write data from/to an SMB3 share, Veeam Backup & Replication uses the account that you provide when adding the Microsoft SMB3 server or cluster. Make sure that this account has Full Control permissions in the security settings for SMB3 shares configured on the scale-out file server.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
