---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_system_requirements.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements


Before you start using Veeam Plug-in for Sangfor aSV, make sure the virtual environment and the backup infrastructure components meet the following requirements.

System Requirements

| Specification | Requirement |
| Virtualization Platform | Veeam Plug-in for Sangfor aSV supports Sangfor HCI versions starting from 6.11.3 |
| Veeam Software | Veeam Backup & Replication version 13.1.0.411 or later must be deployed on the backup server. |
| Workers | Workers process backup workload and distribute backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:   * CPU: 6 vCPU * Memory: 6 GB RAM * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure. |

|  |
| --- |
| Important |
| Workers are backup infrastructure components that are preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support. |

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Sangfor aSV.

Version Compatibility

| Product Release | Veeam Plug-in for Sangfor aSV Build | Veeam Backup & Replication Build |
| 1 | 13.1.0.358 | 13.1.0.411 |

Page updated 2026-07-28

