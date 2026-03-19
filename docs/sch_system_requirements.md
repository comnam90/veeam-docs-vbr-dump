---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_system_requirements.html"
last_updated: "3/12/2026"
product_version: "13.0.1.2067"
---

# System Requirements


Before you start deploying Veeam Plug-in for Scale Computing HyperCore, make sure the virtual environment and the backup infrastructure components meet the following requirements.

System Requirements

| Specification | Requirement |
| Virtualization Platform | Veeam Plug-in for Scale Computing HyperCore supports the following Scale Computing HyperCore versions:   * 9.4.x starting from 9.4.32.218226 * 9.5.x * 9.6.x (required for application-aware processing)   For application-aware processing, Scale Guest Tools must be installed on VMs. |
| Veeam Software | Veeam Backup & Replication version 13.0.1.1071 or later must be deployed on the backup server. |
| Workers | Workers process backup workload and distribute backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:   * CPU: 6 vCPU * Memory: 6 GB RAM * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure. |

|  |
| --- |
| Important |
| Workers are backup infrastructure components that are preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support.  For backup servers running Microsoft Windows, Scale Computing HyperCore version 9.6.6 or later is compatible only with the following OS versions:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows 11 |

Version Compatibility

Version Compatibility

| Product Release | Veeam Plug-in for Scale Computing HyperCore Build | Veeam Backup & Replication Build |
| 3 | 13.3.0.81 | 13.0.1.1071 |
| 2 | 13.2.0.245 | 13.0.1.1071 |
| 1.1 | 12.1.1.4 | 12.3.2.3617 |


