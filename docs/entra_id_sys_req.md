---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_sys_req.html"
last_updated: "2/27/2026"
product_version: "13.0.1.1071"
---

# System Requirements


System Requirements

| Specification | Requirement |
| Veeam Backup & Replication | Veeam Backup & Replication version 13.0.1 must be deployed on the backup server. |
| Backup server | The backup server must meet the system requirements listed in the section [System Requirements](system_requirements.md). |
| Veeam Backup & Replication console | 64-bit versions of the following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2, 23H2, 24H2) * Microsoft Windows 10 (versions 1909 to 22H2) * Microsoft Windows 10 LTS (versions 21H2 LTSC, 22H2 GA)   Other system requirements for the Veeam Backup & Replication console are listed in section [Veeam Backup & Replication Console System Requirements](system_requirements.md). |
| Backup proxy | The general-purpose backup proxy must meet the system requirements listed in section [System Requirements](system_requirements.md). |
| Microsoft Entra ID backup repository | The Microsoft Entra ID backup repository stores tenant backups. This repository is based on a PostgreSQL instance. The requirements for this instance are the same as for the PostgreSQL instance that stores configuration database on the backup server. For more information, see the Configuration Database row in section [Backup Server System Requirements](system_requirements.md).  Note: It is also recommended that you adjust the settings of the PostgreSQL instance that you plan to use as the Microsoft Entra ID backup repository. For more information, see section [Adjusting PostgreSQL Instance Configuration](postgresql_instance_configuration.md). |
| Cache repository | The cache repository stores temporary cache files for log processing. This repository must meet system requirements described in section [Cache Repository System Requirements](system_requirements.md). |
| Log backup repository | The primary and secondary log backup repositories store audit and sign-in log backups and their copies. These repositories must meet requirements described in section [Backup Repository System Requirements](system_requirements.md).  For information on which types of repositories can be used as primary and secondary repositories, see [Configuring Repositories](entra_id_configure_repo.md). |


