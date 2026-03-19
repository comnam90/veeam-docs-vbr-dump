---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_system_requirements.html"
last_updated: "3/16/2026"
product_version: "13.0.1.2067"
---

# System Requirements


Before you start using Veeam Plug-in for HPE Morpheus VM Essentials, make sure the virtual environment and the backup infrastructure components meet the following requirements.

System Requirements

| Specification | Requirement |
| Hypervisor | Kernel-based Virtual Machine (KVM) must be installed on x86 hardware that supports virtualization capabilities. |
| Virtualization Platform | Veeam Plug-in for HPE Morpheus VM Essentials supports HPE Morpheus VM Essentials and HPE Morpheus Enterprise Software versions 8.0.13-2 (and later) and 8.1. The following versions of the HPE Morpheus VM Essentials components are required:   * host agent: 3.1.3 * morpheus-ws-node package:3.3.19-1 * alletra plugin: 1.8.1   Veeam Plug-in for HPE Morpheus VM Essentials requires at least one datastore of the Directory Pool, NFS Pool, GFS2 Pool type configured in the HPE Morpheus VM Essentials manager. |
| Veeam Software | Veeam Backup & Replication version 13.0.1.1071 or later must be deployed on the backup server. |
| Workers | Workers process backup workloads and distribute backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:   * CPU: 6 vCPU * Memory: 6 GB RAM * Disk Space: 100 GB for product installation and logs   With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure. |

|  |
| --- |
| Important |
| Workers are backup infrastructure components that are preconfigured for optimal performance. That is why you must not install any software on VMs running as workers or make any configuration changes to them unless you are requested by Veeam Customer Support. |

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for HPE Morpheus VM Essentials.

Version Compatibility

| Product Release | Veeam Plug-in for HPE Morpheus VM Essentials Build | Veeam Backup & Replication Build | Worker OS Version |
| 1 | 13.1.0.271 | 13.0.1.1071 | Veeam JeOS 9.2 |


