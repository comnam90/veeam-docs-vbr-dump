---
title: "Veeam Infrastructure Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_via.html"
last_updated: "3/4/2026"
product_version: "13.0.1.1071"
---

# Veeam Infrastructure Appliance


Veeam Infrastructure Appliance is a Linux distribution delivered by Veeam as a bootable JeOS (Just Enough Operating System) ISO file. It contains only services and components required to deploy and manage Veeam infrastructure components with specific roles including hardened repositories and backup proxies.

Veeam Infrastructure Appliance

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum running at 1 GHz or higher.  Memory: 8 GB RAM.  Disk 1: 120 GB1 minimum. This disk hosts Veeam JeOS, Veeam Backup & Replication software and instant recovery cache.  Disk 2: 120 GB1 minimum. This disk hosts Veeam applications data, therefore recommended sizing depends on your backup storage needs. Any additional disks found in the system will be automatically joined with Disk 2 into the single Logical Volume Manager (LVM) spanned volume.  Note: Veeam Infrastructure Appliance only supports local disks and hardware RAID. RAID controller with battery or capacitor backed write cache is highly recommended for performance and reliability reasons.  Network: 1 Gbps or faster for on-site backup and replication, 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.  Server Hardware: Veeam offers [Veeam Ready - Appliance](https://www.veeam.com/solutions/alliance-partner/integrations-qualifications.html?programCategory=veeam-ready-appliance) certification for hardware vendors. This certification ensures verified and certified compatibility, delivering an optimal customer experience through additional requirements for direct technical collaboration between vendors. Veeam also acknowledges that some customers may need to use existing hardware. As current compatibility guidance, we expect that most systems listed on the [RHEL Hardware Compatibility List (HCL)](https://catalog.redhat.com/en/search?searchType=Hardware&certified_RedHat_Platforms=Red+Hat+Enterprise+Linux&certified_architectures=x86_64) will be compatible with Veeam Software Appliance  1 Here GB is considered as 10^9 bytes. |
| Software | Veeam Infrastructure Appliance ISO deployment to a virtual machine is supported, provided the hypervisor is listed as supported by Veeam. |

For more information, see the [Deploying Linux Infrastructure Components](linux_infrastructure.md) section.


