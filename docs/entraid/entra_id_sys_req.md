---
title: "System Requirements"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_sys_req.html"
last_updated: "12/18/2025"
product_version: "13.0.1.1071"
---

# System Requirements


| Specification | Requirement |
| --- | --- |
| Veeam Backup & Replication | Veeam Backup & Replication version 13.0.1 must be deployed on the backup server. |
| Backup server | The backup server must meet the system requirements listed in the Veeam Backup & Replication User Guide, section [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#backup_server). |
| Veeam Backup & Replication console | 64-bit versions of the following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2, 23H2, 24H2) * Microsoft Windows 10 (versions 1909 to 22H2) * Microsoft Windows 10 LTS (versions 21H2 LTSC, 22H2 GA)   Other system requirements for the Veeam Backup & Replication console are listed in the Veeam Backup & Replication User Guide, section [Veeam Backup & Replication Console System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#console). |
| Backup proxy | The general-purpose backup proxy must meet the system requirements listed in the Veeam Backup & Replication User Guide, section [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#general-purpose-backup-proxy). |
| Microsoft Entra ID backup repository | The Microsoft Entra ID backup repository stores tenant backups. This repository is based on a PostgreSQL instance. The requirements for this instance are the same as for the PostgreSQL instance that stores configuration database on the backup server. For more information, see the Configuration Database row in [Backup Server System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#backup_server) section in the Veeam Backup & Replication User Guide.  Note: It is also recommended that you adjust the settings of the PostgreSQL instance that you plan to use as the Microsoft Entra ID backup repository. For more information, see Veeam Backup & Replication User Guide, section [Adjusting PostgreSQL Instance Configuration](https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_instance_configuration.html?ver=13). |
| Cache repository | The cache repository stores temporary cache files for log processing. This repository must meet system requirements described in the [Cache Repository System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#cache_repo) section in the Veeam Backup & Replication User Guide. |
| Log backup repository | The primary and secondary log backup repositories store audit and sign-in log backups and their copies. These repositories must meet requirements described in the [Backup Repository System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13#cache_repo) section in the Veeam Backup & Replication User Guide.  For information on which types of repositories can be used as primary and secondary repositories, see [Configuring Repositories](entra_id_configure_repo.md). |


