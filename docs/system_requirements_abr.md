---
title: "Application Backup Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_abr.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Application Backup Repository


An application backup repository is based on Veeam Hardened Repository deployed from the Veeam Infrastructure Appliance ISO file.

Veeam Infrastructure Appliance is a Linux distribution delivered by Veeam as a bootable JeOS (Just Enough Operating System) ISO file. It contains only services and components required to deploy and manage Veeam infrastructure components with specific roles.

Application Backup Repository

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 4 cores (vCPUs) minimum running at 1 GHz or higher. Using multi-core processors improves data processing performance.  Memory: 8 GB RAM. The actual size of memory required may be larger and depends on the amount of data to back up. Using faster memory improves data processing performance.  Disk 1: 120 GB1 minimum. This disk hosts Veeam JeOS, Veeam Backup & Replication software and instant recovery cache.  Additional disks: Recommended sizing depends on your backup storage needs. Note that if storage utilization reaches 97% of the storage pool capacity, snapshot creation stops. If storage utilization exceeds 80% of the storage pool capacity, the system performance may degrade.  Any additional empty disks can be automatically joined into one storage pool when deploying the application backup repository. For more information, see [Deploying Application Backup Repository](deploy_abr.md).  Note: Veeam Infrastructure Appliance only supports local disks and hardware RAID. RAID controller with battery or capacitor backed write cache is highly recommended for performance and reliability reasons.  Network: 1 Gbps or faster for on-site backup and replication, 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.  1 Here GB is considered as 10^9 bytes. |
| Software | Veeam Infrastructure Appliance ISO deployment to a virtual machine is supported, provided the hypervisor is listed as supported by Veeam. |

For more information, see the [Deploying Linux Infrastructure Components](linux_infrastructure.md) section.

Page updated 2026-07-30

