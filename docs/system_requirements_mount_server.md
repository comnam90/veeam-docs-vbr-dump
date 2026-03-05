---
title: "Mount Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_mount_server.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Mount Server


Mount servers can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

Mount Server

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum, plus 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance.  Memory: 4 GB RAM, plus not less than 1 GB RAM for each concurrently processed machine disk.  The following jobs consume not less than 400 MB RAM per guest VM on mount server:   * Windows file level restore   The following jobs consume 1 GB RAM per guest VM disk on mount server + 100 MB RAM per VM:   * SureBackup * Instant Recovery * Instant Disk Recovery   Disk Space: 1.4 GB for product installation and 4.5 GB for Microsoft .NET Framework 4.7.2 installation. If Microsoft .NET Framework 4.7.2 is not installed on the machine, Veeam Backup & Replication will install it automatically.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the Linux operating systems:   * RHEL 9.6 * Rocky Linux 9.6   Note: If you use RHEL or Rocky Linux version 9 or later, and do not use [Veeam Infrastructure Appliance](linux_infrastructure.md), you must install the following packages before adding the server to the backup infrastructure: aspnetcore-runtime (version 8.0 or later), bindfs, samba-client and ntfs-3g.  Note: If you use the Microsoft Windows-based mount server and plan to restore guest OS files from workloads that run Microsoft Windows with ReFS volumes, or from workloads with data deduplication enabled for some volumes, you must assign the mount server role to the machines running the required OS versions. For more information, see [ReFS](guest_restore_before_you_begin.md#refs) and [Data Deduplication](guest_restore_before_you_begin.md#dedup) subsections in Restoring VM Guest OS Files. |

For more information, see the [Mount Server](mount_server.md) section.


