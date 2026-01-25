---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veo_systemreqs.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# System Requirements


The system requirements depend on whether you want to use an image-level backup created with native Veeam Backup & Replication functionality or an application backup created with Veeam Plug-In for Oracle RMAN.

Data Recovery from Image-Level Backups

This section lists system requirements that are relevant when recovering data from image-level backups created by Veeam Backup & Replication.

| Component | Requirement |
| --- | --- |
| Oracle Database on Windows OS | Veeam Explorer for Oracle supports restore of Oracle Database running on the following Microsoft Windows operating systems:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  Veeam Explorer for Oracle supports restore of the following Oracle Database versions on Microsoft Windows machines:  * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2 |
| Oracle Database on Linux OS | Veeam Explorer for Oracle supports restore of Oracle Database running on the following Linux distributions:  * RHEL 8.4 to 9.4 * SLES 12 SP5, 15 SP3 or later * Oracle Linux 7 (UEK3) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK)  Veeam Explorer for Oracle supports restore of the following Oracle Database versions on Linux machines:  * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2 |

Restore from RMAN Plug-in Backups

This section lists system requirements that are relevant when restoring data from backups created with Veeam Plug-In for Oracle RMAN (in managed or standalone mode).

| Component | Requirement |
| --- | --- |
| Oracle Database on Windows OS | Veeam Explorer for Oracle supports restore from RMAN plug-in backups of Oracle Database running on the following Microsoft Windows operating systems:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   Veeam Explorer for Oracle supports restore from RMAN plug-in backups of the following versions of Oracle Database on Windows machines:   * Oracle Database 21c  * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2   Notes:   * Oracle Express Edition (XE) is not supported. * Oracle databases residing in OS-level containerized environments (for example: Docker, Podman) are not supported. * Support for Oracle database 23ai is limited to virtual machines in cloud deployments (for example: Oracle Cloud Infrastructure, Oracle Exadata Cloud) and Oracle Engineered Systems (for example: Oracle Exadata, Oracle Database Appliance). |
| Oracle Database on Linux OS | Veeam Explorer for Oracle supports restore from RMAN plug-in backups of Oracle Database running on the following Linux distributions:   * SUSE Linux Enterprise Server 12 SP5, 15 SP3 and SP7 (x86 and x86\_64) * RHEL 8.4 – 9.x, 10.0 including Extended Update Support Add-On * Oracle Linux 7 – 9.x * CentOS 6.4 – 8.x (For non-production environments, as it is not officially supported by Oracle for their databases)   Veeam Explorer for Oracle supports restore from RMAN plug-in backups of the following versions of Oracle Database on Linux machines:   * Oracle Database 23ai * Oracle Database 21c  * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c * Oracle Database 11g Release 2   Notes:   * Oracle Express Edition (XE) is not supported. * Oracle databases residing in OS-level containerized environments (for example: Docker, Podman) are not supported. * Support for Oracle database 23ai is limited to virtual machines in cloud deployments (for example: Oracle Cloud Infrastructure, Oracle Exadata Cloud) and Oracle Engineered Systems (for example: Oracle Exadata, Oracle Database Appliance). |


