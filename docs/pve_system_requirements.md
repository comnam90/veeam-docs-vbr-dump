---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_system_requirements.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Before you start using Veeam Plug-in for Proxmox VE, make sure the virtual environment and the backup infrastructure components meet the following requirements.

| Specification | Requirement |
| --- | --- |
| Hypervisor | Proxmox VE must be installed on x86 hardware that supports virtualization capabilities. For more information on recommended hardware specifications, see [Proxmox VE documentation](https://www.proxmox.com/en/products/proxmox-virtual-environment/requirements). |
| Virtualization Platform | Veeam Plug-in for Proxmox VE supports Proxmox Virtual Environment versions 8.2–9.1 installed using the official ISO image provided by Proxmox.  Veeam Plug-in for Proxmox VE requires at least one file-level storage configured in Proxmox Virtual Environment.  For application-aware processing and application item restore operations, the [QEMU Guest Agent](https://pve.proxmox.com/wiki/Qemu-guest-agent) must be installed on VMs and enabled in Proxmox Virtual Environment — before backups are created. |
| Veeam Software | Veeam Backup & Replication version 13.0.1.180 or later must be deployed on the backup server. |
| Workers | Workers process backup workload and distribute backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:   * CPU: 6 vCPU * Memory: 6 GB RAM * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure. |

|  |
| --- |
| Important |
| Workers are backup infrastructure components that are preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support. |

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Proxmox VE.

| Product Release | Veeam Plug-in for Proxmox VE Build | Veeam Backup & Replication Build | Worker OS Version |
| --- | --- | --- | --- |
| 3 | 13.3.0.237 | 13.0.1.180 | Rocky Linux 9.2 |
| 2 | 13.2.0.457 | 13.0.0.4967 | Rocky Linux 8.10 |
| 1.5 | 12.1.5.17 | 12.3.2.3617 |
| 1.3 | 12.1.3.217 | 12.3.2.3617  12.3.1.1139  12.3.0.310 |
| 1.1 | 12.1.1.1024 | 12.3.0.310  12.2.0.334 |


