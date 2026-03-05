---
title: "Gateway Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_gateway.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Gateway Server


Gateway servers can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage gateway servers on supported operating systems of your choice.

Gateway Server

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum.  Memory: 4 GB RAM, plus up to 4 GB RAM for each concurrently processed machine, file share or object storage. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md). For RAM allocation recommendations for unstructured data backup, see [Limitations and recommendations for unstructured data backup](#nas_recommendations).  Disk space: 750 MB for Microsoft Windows-based proxies; 400 MB for Linux-based proxies.  Note: If a unstructured data backup stored in an object storage does not have metadata in the cache repository, during the restore or health check operation this metadata will be downloaded to the gateway server. That can consume up to 80% of the gateway server disk space.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  Note that the fast cloning on ReFS volumes feature requires a Microsoft Windows gateway server.  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 13.1 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Note: If you use RHEL or Rocky Linux version 9 or later, and do not use [Veeam Infrastructure Appliance](linux_infrastructure.md), you must install the following packages before adding the server to the backup infrastructure: cifs-utils (for the gateway server assigned to a SMB backup repository) or nfs-utils (for the gateway server assigned to a NFS backup repository). |

For more information, see the [Gateway Server](gateway_server.md) section.


