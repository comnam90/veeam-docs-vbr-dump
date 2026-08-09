---
title: "System Requirements for Microsoft Windows"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_db2_system_requirements_win.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements for Microsoft Windows


Before you start using Veeam Plug-In for IBM Db2 on machines running Microsoft Windows, make sure the requirements listed in this section are met.

|  |
| --- |
| Note |
| The following system requirements apply to Veeam Plug-In for IBM Db2 for Microsoft Windows operating in the standalone mode. The managed operation mode is not supported. For details on operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes). |

System Requirements for Microsoft Windows

| Specification | Requirement |
| OS | Veeam Plug-In is supported for the following Microsoft Windows versions:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   For additional information about supported Microsoft Windows versions that are listed for supported configurations of IBM Db2, see [this IBM article](https://www.ibm.com/support/pages/system-requirements-ibm-db2-linux-unix-and-windows). |
| Software | Microsoft .NET Framework 4.6 is included in the Veeam Plug-In Redistributable. During the deployment process, Veeam Backup & Replication checks whether Microsoft .NET Framework 4.6 is available on the target computer. If Microsoft .NET Framework 4.6 is missing, Veeam Backup & Replication will install the missing software automatically. |
| IBM Db2 | Veeam Plug-In for IBM Db2 supports the following configurations of IBM Db2:   * Versions: 11.1, 11.5 and 12.1 * Editions: Standard, Advanced * Environments: standalone servers, high availability disaster recovery (HADR), failover clusters   In failover cluster environments, Veeam Plug-In supports clustered databases managed with Windows Server Failover Clustering. HADR environments are also supported. |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports different on versions of Veeam Plug-In depending on which OS is running on the backup server:   * Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported. * Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.   Keep in mind that if you use an earlier Veeam Plug-In build than the one that is included in the installation ISO file of your Veeam Backup & Replication version, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474). |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway.  For communication between the Veeam backup infrastructure and servers that host databases to be backed up, one of the following authentication protocols is required:   * Kerberos. To learn more, see [Kerberos Authenticationkerberos\_authentication](kerberos_authentication.md).  * Windows New Technology LAN Manager (NTLM).   As NTLM is provided by Microsoft, only the Veeam Backup & Replication server running on the Microsoft Windows OS supports NTLM. |

Page updated 2026-07-24

