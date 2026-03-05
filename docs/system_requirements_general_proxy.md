---
title: "General-Purpose Backup Proxy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_general_proxy.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# General-Purpose Backup Proxy


General-purpose backup proxies can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

The following table shows the minimum system requirements for a general-purpose backup proxy used for unstructured data backup and Veeam Agent and storage system snapshot integration.

General-Purpose Backup Proxy

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum. 4 cores (vCPUs) are recommended (2 cores are required) for each additional concurrent task. Using multi-core processors enhances data processing performance and enables the processing of more tasks simultaneously.  Memory: [For unstructured data backup] 4 GB RAM plus 4 GB RAM for each concurrent task.  [For Veeam Agent and storage system snapshot integration] 2 GB RAM plus 1 GB RAM for each concurrent task.  Using faster memory improves data processing performance. For all-in-one installations, where the server performs several roles, it must have enough memory resources for all components.  Disk Space: 300 MB.  Network: High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 12.11 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Note: The VSS snapshot creation for SMB File Shares feature requires that all requirements listed in [this Veeam KB article](https://www.veeam.com/kb3099) are met.  [For Veeam Agent and storage system snapshot integration] Backup proxies and Veeam agent computers must run Microsoft Windows Server OS versions. Backup proxies cannot run the OS versions that are earlier than the Veeam Agent computer OS version. |

For more information, see the [General-Purpose Backup Proxies](backup_proxy_general.md) section.


