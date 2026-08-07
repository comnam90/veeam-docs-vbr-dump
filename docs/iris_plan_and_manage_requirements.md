---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_plan_and_manage_requirements.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements


Make sure that components in the Epic EHR System Protection management infrastructure meet the system requirements listed in this section.

Veeam Backup Server

For details on system requirements for the Veeam backup server and other Veeam Backup & Replication components, see [System Requirements](system_requirements.md) for Veeam Backup & Replication.

Computer with InterSystems IRIS Instance

A computer with instances you want to protect using Epic EHR System Protection must meet the following requirements:

* Licensing: Veeam Universal License (VUL); Enterprise Plus edition or higher.
* Platforms: VMware vSphere VMs with pass-through RDM, and physical machines.
* Containerized deployments are not supported; the InterSystems IRIS instance must run directly on the host.
* Backup proxies: Linux-based proxies only.
* Storage systems: must be compatible with the Universal Storage API.

Computer with InterSystems IRIS Instance

| Specification | Requirement |
| OS | Epic EHR System Protection management infrastructure supports InterSystems IRIS instance deployments running on the 64-bit versions of the following distributions:   * RHEL 9.8 – 10.2 * Ubuntu 22.04 – 24.04 LTS * SLES 15 SP6, 15 SP7 |
| Veeam Backup & Replication | Veeam Backup & Replication 13.1 supports management of InterSystems IRIS. |
| Database | Veeam Backup & Replication supports the following versions of the InterSystems IRIS Data Platform:   * 2025.3 * 2025.2 * 2025.1 * 2024.1 * 2023.1 |
| File Systems | Veeam Backup & Replication supports consistent snapshot-based data backup for the following file systems:   * XFS (DAT/WIJ) * Ext4 |
| Storage Systems | Veeam Backup & Replication supports InterSystems IRIS instance deployments with integrated Universal Storage API storage systems based on the OS of the backup server.  Microsoft Windows-based backup servers:   * DataCore SANsymphony * Dell PowerMax * Dell PowerStore * Dell SC Series (formerly Compellent) * Fujitsu ETERNUS AF and DX Series * Hitachi VSP/VSP One Block * HPE XP * IBM FlashSystem (formerly Spectrum Virtualize, includes IBM StorWize and IBM SVC) * Infinidat InfiniBox F-Series * NEC Storage M Series * NetApp SolidFire/HCI * Pure Storage FlashArray * Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)   Linux-based backup servers:   * Hitachi VSP/VSP One Block * HPE XP * IBM FlashSystem (formerly Spectrum Virtualize, includes IBM StorWize and IBM SVC)   For more information on storage system models and connectivity, see [Storage Systems](system_requirements_storage_systems.md). |

Page updated 2026-08-06

