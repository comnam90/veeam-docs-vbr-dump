---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vlab_before_you_begin_vm.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a virtual lab, check the following prerequisites:

* A valid license for Enterprise edition of Veeam Backup & Replication must be installed on the backup server.
* The ESXi host on which you plan to deploy a virtual lab must have a VMkernel interface. Otherwise the vPower NFS datastore will not be mounted on the ESXi host. For more information, see [Veeam vPower NFS Service](vpower_nfs_service.md).
* If you plan to use the advanced multi-host networking mode for VM replicas verification, you must configure a DVS beforehand. For more information, see [Advanced Multi-Host Virtual Labs](surereplica_advanced_mutihost.md).

|  |
| --- |
| Note |
| Starting from Veeam Backup & Replication 12, you can verify Microsoft Hyper-V backups and Veeam Agent backups using VMware vSphere virtual lab. To learn about SureBackup limitations for Veeam Agent backups, see [Veeam Agent Backup](agents_recovery_verification.md). |

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
