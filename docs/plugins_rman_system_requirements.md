---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_rman_system_requirements.html"
last_updated: "2/9/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Before you start using Veeam Plug-In for Oracle RMAN, make sure the following requirements are met.

|  |
| --- |
| Note |
| The following system requirements apply to Veeam Plug-In for Oracle RMAN operating in the standalone mode.  For more information on system requirements for Veeam Plug-In managed by Veeam Backup & Replication, see [System Requirements for Managed Veeam Plug-Ins](plan_and_manage_requirements.md#compvpor). |

| Specification | Requirement |
| --- | --- |
| OS | Veeam Plug-In for Oracle RMAN is supported for the following Microsoft Windows versions:  * Microsoft Windows Server 2025  * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2  Veeam Plug-In for Oracle RMAN is supported for the following x86\_64 versions of Linux distributions:  * SUSE Linux Enterprise Server 12 SP5, 15 SP3 and SP7 (x86 and x86\_64) * RHEL 8.4 – 9.x, 10.0 including Extended Update Support Add-On * Oracle Linux 7 – 9.x * CentOS 6.4 – 8.x: For non-production environments, as it is not officially supported by Oracle for their databases.  Veeam Plug-In for Oracle RMAN is supported for the following Unix versions:   * Oracle Solaris 10, 11 (x86\_64, SPARC) * IBM AIX 6.1, 7.1, 7.2, 7.3 |
| Software | [For Microsoft Windows computers] Microsoft .NET Framework 4.6 is included in the Veeam Plug-In for Oracle RMAN Redistributable. During the deployment process, Veeam Backup & Replication checks whether Microsoft .NET Framework 4.6 is available on the target computer. If Microsoft .NET Framework 4.6 is missing, Veeam Backup & Replication will install missing software automatically. |
| Oracle database | Veeam Plug-In for Oracle RMAN supports Standard and Enterprise Editions of the following Oracle Database versions:  * Oracle Database 23ai * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c * Oracle Database 11g Release 2 |
| Supported Oracle RMAN features | Veeam Plug-In for Oracle RMAN supports the following Oracle RMAN features:   * Veeam Plug-In will be registered as an SBT\_TAPE device. All Oracle RMAN functionality that is supported with the SBT\_TAPE device type will work. For example, Automatic Storage Management (Oracle ASM) and Container DBs (CDBs). * Veeam Plug-In supports Oracle Real Application Clusters (Oracle RAC). Other cluster databases are not supported. |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports different on versions of Veeam Plug-In depending on which OS is running on the backup server:   * Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported. * Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.   Keep in mind that if you use an earlier Veeam Plug-In build than the one that is included in the installation ISO file of your Veeam Backup & Replication version, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474). |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway. |


