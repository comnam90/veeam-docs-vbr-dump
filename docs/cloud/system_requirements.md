---
title: "System Requirements"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/system_requirements.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Make sure that servers on which you plan to deploy Veeam Cloud Connect infrastructure components meet system requirements listed in this section.

Cloud Gateway

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86 or x86-64 processor with 8 cores (vCPUs) minimum.  Memory: 8 GB RAM for up to 500 concurrent tenant tasks.  Disk Space: 300 MB for Cloud Gateway service installation.  Network: 1 Gbps LAN or faster. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)   64-bit versions of the following Linux distributions are supported:   * RHEL 9.6 * Veeam Infrastructure Appliance |

SP Veeam Backup Server

To learn about system requirements for Veeam backup servers deployed on the SP side, see the [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#backup_server) section in the Veeam Backup & Replication User Guide.

In addition to requirements listed in the Veeam Backup & Replication User Guide, the SP backup server must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | Memory: 8 GB RAM minimum, 16 GB RAM for installations with more than 100 parallel tenant tasks. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021) |

|  |
| --- |
| Note |
| Linux distributions are not supported for the Veeam backup servers deployed on the SP side. |

The following recommendations help improve data processing performance for the SP backup server:

| Specification | Recommendation |
| --- | --- |
| SQL Database | It is recommended to use an SQL database installed on a dedicated server.  The following versions of PostgreSQL are supported:   * PostgreSQL 17.x (PostgreSQL 17.6 is included in the Veeam Backup & Replication 13 setup, but we strongly recommend to [download](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads) and install the latest PostgreSQL 17.x version) * PostgreSQL 15.x * PostgreSQL 14.x   The following versions of Microsoft SQL Server are supported:   * Microsoft SQL Server 2022 Standard or Enterprise Edition * Microsoft SQL Server 2019 Standard or Enterprise Edition * Microsoft SQL Server 2017 Standard or Enterprise Edition * Microsoft SQL Server 2016 Standard or Enterprise Edition |

For installations with high loads (up to 1,000 parallel tenant tasks), consider performance tuning. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4217).

Tenant Veeam Backup Server

To learn about system requirements for Veeam backup servers deployed on the tenant side, see the [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#backup-server) section in the Veeam Backup & Replication User Guide.

In addition to requirements listed in the Veeam Backup & Replication User Guide, the tenant backup server must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)   For Linux-based server, Veeam Software Appliance ISO deployment to a virtual machine is supported for all hypervisors for which Veeam offers host-based VM backup functionality. For details, see [Supported Platforms, Applications and Workloads](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html). |

Cloud Repository

To learn about system requirements for backup repositories used as cloud repositories, see the [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#repo) section in the Veeam Backup & Replication User Guide.

Backup Proxy

To learn about system requirements for backup proxies used in the Veeam Cloud Connect infrastructure, see the [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13) section in the Veeam Backup & Replication User Guide.

WAN Accelerator

To learn about system requirements for WAN accelerators deployed on the SP side and on tenant side, see the [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#wan) section in the Veeam Backup & Replication User Guide.


