---
title: "Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_workers.html"
last_updated: "2/26/2026"
product_version: "13.0.1.1071"
---

# Workers


Workers process the backup workload and distribute the backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:

Workers

| Specification | Requirement |
| Hardware | CPU: 6 cores (vCPUs).  Memory: 6 GB RAM  Disk Space: 100 GB for product installation and logs. |

With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure.

For more information, see the [Nutanix AHV](nutanix_ahv.md), [Proxmox Virtual Environment](proxmox_ve.md), [oVirt KVM](olvm_rhv.md) and [Scale Computing HyperCore](sc_hypercore.md) sections.


