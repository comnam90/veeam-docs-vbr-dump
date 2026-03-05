---
title: "Backup Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_backup_repo.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Backup Repository


A Linux Hardened Repository server can be deployed from the [Veeam JeOS](linux_infrastructure.md) image by selecting the corresponding option. This enables certificate-based authentication over secure, industry-leading communication protocols, eliminates the need to open SSH and additional ports, and minimizes the potential attack surface.

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage the following operating systems on your own.

Backup Repository

| Specification | Requirement |
| Hardware | CPU: x86-64 processor. The number of cores depends on the concurrent task settings. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#repo).  Memory: 4 GB RAM, plus not less than 1 GB RAM for each concurrently processed machine disk. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#repo).  [For unstructured data backup] Not less than 4 GB RAM for each concurrently processed unstructured data source (file share or object storage); in case of deduplicating storage appliances, up to 8 GB RAM. Additionally, 1GB RAM is required for indexing each 200 million objects (files and folders). In case of all-in-one installations for unstructured data backup, where the server performs several roles, it must have enough memory resources for all components.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  Note that there can be some issues with Microsoft Windows Server 2025 with the ReFS file system. For details, see [this Veeam KB article](https://www.veeam.com/kb2792).  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 13.1 * Oracle Linux 7 to 10 * RHEL 8.6 to 10.0  * Rocky Linux 9 and 10 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 or later, 16 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Bash shell and SSH are required to deploy the management agent (SSH connection is not required for updating Veeam components and can be disabled afterwards).  For advanced XFS integration (fast clone), only the following 64-bit Linux distributions are supported:   * Debian 11.0 to 13.1  * RHEL 8.6 to 10.0  * Rocky Linux 9.4 to 10.0  * SLES 15 SP3 or later, 16 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   For other distributions, XFS integration support is experimental, with kernel version 5.4 or later recommended. For more information, see [this Veeam KB article](https://www.veeam.com/kb2976). |

For more information, see the [Backup Repositories](backup_repository.md) section.

|  |
| --- |
| Note |
| Consider the following:   * If you plan to use a Microsoft Windows backup repository with Data Deduplication, make sure that you set up the Microsoft Windows server correctly. For more information, see [this Veeam KB article](https://www.veeam.com/kb1893). * In rare cases, Veeam backups may become corrupted when stored on the exFAT file system. We strongly discourage using the exFAT filesystem for backup storage when attached to Windows 10 or Windows Server 2019 and later. For more information, see [this Veeam KB article](https://www.veeam.com/kb4233). |


