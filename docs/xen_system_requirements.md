---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_system_requirements.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements


Before you start using Veeam Plug-in for Xen, make sure the virtual environment and the backup infrastructure components meet the following requirements.

System Requirements

| Specification | Requirement |
| Virtualization Platform | Veeam Plug-in for Xen supports the following platforms:   * XCP-ng 8.3 and later * Citrix XenServer 8.4 and later (changed block tracking requires a paid license)   Veeam Plug-in for Xen requires at least one storage repository of a supported type configured in the pool: Local EXT, NFS, LVM, LVM over iSCSI, LVM over HBA, LVM over Fibre Channel, GFS2, LINSTOR, ZFS, XFS, GlusterFS, SMB and File. |
| Veeam Software | Veeam Backup & Replication version 13.1.0.411 or later must be deployed on the backup server. |
| Workers | Workers process backup workloads and distribute backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:   * CPU: 6 vCPU * Memory: 6 GB RAM * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure. |

|  |
| --- |
| Important |
| Workers are backup infrastructure components that are preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support. |

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Xen.

Version Compatibility

| Product Release | Veeam Plug-In for Xen Build | Veeam Backup & Replication Build | Worker OS Version |
| 1 | 13.1.0.295 | 13.1.0.411 | CIQ Rocky Linux 9.2 |

Page updated 2026-07-28

