---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_system_requirements.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements


Before you start using Veeam Plug-in for Universal Hypervisor API, make sure the virtual environment and the backup infrastructure components meet the following requirements.

System Requirements

| Specification | Requirement |
| Hypervisor | Kernel-based Virtual Machine (KVM) must be installed on x86 hardware that supports virtualization capabilities. |
| Virtualization Platform | Veeam Plug-in for Universal Hypervisor API supports the following virtual environments:   * Platform9 version 2026.4 or later. * VergeOS version 26.1.7 or later. |
| Workers | Workers process backup workloads and distribute backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:   * CPU: 6 vCPU * Memory: 6 GB RAM * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure. |

|  |
| --- |
| Important |
| Workers are backup infrastructure components that are preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support. |

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Universal Hypervisor API.

Version Compatibility

| Product Release | Veeam Plug-in for Universal Hypervisor API Build | Veeam Backup & Replication Build | Worker OS Version |
| 1 | 13.1.0.191 | 13.1.0.411 | Veeam JeOS 9.6 |

Page updated 2026-07-30

