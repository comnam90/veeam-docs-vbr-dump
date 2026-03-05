---
title: "WAN Accelerator"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_wan_accelerator.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# WAN Accelerator


WAN accelerators can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled via the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

WAN Accelerator

| Specification | Requirement |
| Hardware | CPU: x86-64 processor. Using multi-core processors improves data processing performance, and is highly recommended on WAN links faster than 10 Mbps.  Memory: 8 GB RAM. Using faster memory improves data processing performance.  Disk Space: Disk space requirements depend on the WAN Accelerator role. Source WAN Accelerator requires 20 GB per 1 TB of source data to store digests of data blocks of source VM disks. Disk space consumption is dynamic and changes as unique VMs are added to (or removed from) jobs with WAN Acceleration enabled. Target WAN Accelerator requires global cache size as defined by user (fixed amount). Disk space is reserved immediately upon selecting the WAN Accelerator as a target one in any job. For more information, see [WAN Accelerator Sizing](wan_accelerator_sizing.md).  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported1:   * Debian 11.0 to 12.9 * Oracle Linux 7 (UEK3) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK) * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 or later * Ubuntu: 20.04 LTS, 22.04 LTS, 24.04 LTS |

For more information, see the [WAN Accelerators](wan_accelerator.md) section.

|  |
| --- |
| Note |
| Global cache is not leveraged by source WAN accelerators, or by WAN accelerators operating in the High bandwidth mode, so it does not need to be allocated and populated in such cases. |


