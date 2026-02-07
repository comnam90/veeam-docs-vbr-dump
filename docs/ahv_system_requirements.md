---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_system_requirements.html"
last_updated: "2/6/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Before you start using Veeam Plug-in for Nutanix AHV, make sure the Nutanix AHV cluster or Prism Central and the backup infrastructure components meet the following requirements.

| Specification | Requirement |
| --- | --- |
| Virtualization Platform | * Veeam Plug-in for Nutanix AHV is compatible with:  * Nutanix AOS versions 6.8.1.6 and above * Prism Central version pc.2022.6–pc.2024.3.1.10, pc.7.3 and above except 7.3.1.2 and 7.5.0  * An IP address of the cluster and the iSCSI Data Service must be configured in Nutanix AHV cluster settings. For more information, see [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:wc-cluster-details-modify-wc-t.html). * UEFI boot must be supported in the Nutanix AHV environment. For more information, see [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v6_8:vm-vm-uefi-support-c.html). * Veeam Plug-in for Nutanix AHV supports Nutanix Cloud Clusters (NC2) used for hybrid multi-cloud deployment. |
| Veeam Software | * Veeam Backup & Replication version 13.0.1.180 (or later) with Veeam Plug-in for Nutanix AHV version 13.9.0.212 (or later) must be deployed on the backup server. |
| Workers | [Workers](ahv_workers.md) process backup workload and distribute backup traffic when transferring data to and from backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated to the worker VM:   * CPU: 6 vCPU * Memory: 6 GB RAM  * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks in parallel. While deploying a new worker or editing settings of an existing one, you can change the maximum number of concurrent tasks. To do that, adjust compute resources allocated to the worker VM according to the recommendations described in section [Sizing Guidelines](ahv_sizing_guide.md#workers). |

|  |
| --- |
| Important |
| Workers are deployed as backup infrastructure components preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support. |

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Nutanix AHV.

| Product Release | Veeam Plug-in for Proxmox VE Build | Veeam Backup & Replication Build | Backup Appliance / Worker OS Version |
| --- | --- | --- | --- |
| 9 | 13.9.0.212 | 13.0.1.180 | CIQ Rocky Linux 9.2 |
| 8 | 13.8.0.582 | 13.0.0.4967 | Rocky Linux 8.10 |
| 7.1 | 12.7.1.12 | 12.3.1.1139 | Rocky Linux 8.10 |
| 7.0 | 12.7.0.172 | 12.3.0.310 |
| 6.1 | 12.6.1.15 | 12.2.0.334 |
| 6.0 | 12.6.0.632 | 12.2.0.334 |
| 5.1 | 12.5.1.8 | 12.1.0.2131 | Ubuntu 22.04 LTS |
| 5.0 | 12.5.0.465 | 12.0.0.1420 |
| 4a | 12.1.4.5 | 12.0.0.1420 | Ubuntu 20.04 LTS |
| 4.0 | 12.0.4.1020 | 12.0.0.1420 |


