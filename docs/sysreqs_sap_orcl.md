---
title: "System Requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sysreqs_sap_orcl.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# System Requirements

In this article

Before you start using Veeam Plug-In for SAP on Oracle, make sure the following requirements are met.

|  |
| --- |
| Note |
| The following system requirements apply to Veeam Plug-In for SAP on Oracle operating in the standalone mode.  For more information on system requirements for Veeam Plug-In managed by Veeam Backup & Replication, see [System Requirements for Managed Veeam Plug-Ins](plan_and_manage_requirements.md#compvpso). |

| Specification | Requirement |
| --- | --- |
| OS | Veeam Plug-In for SAP on Oracle is supported for the following distributions:   * SUSE Linux Enterprise Server versions 12 SP5, 15 SP3 (x86\_64) * RHEL for SAP Applications versions 8.4, 9 (x86\_64) * Oracle Linux versions 7, 8 |
| SAP Software | Veeam Plug-In for SAP on Oracle supports BR\*Tools version 7.20, Patch 42 or later. |
| Oracle Database | Veeam Plug-In for SAP on Oracle supports Standard and Enterprise Editions of the following Oracle Database versions:   * 19c * 18c * 12c * 11g Release 2   Note. Oracle Express Edition (XE) and Oracle Real Application Cluster (RAC) environment are not supported. |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports different on versions of Veeam Plug-In depending on which OS is running on the backup server:   * Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported. * Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.   Keep in mind that if you use an earlier Veeam Plug-In build than the one that is included in the installation ISO file of your Veeam Backup & Replication version, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474). |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway. |

Page updated 10/14/2025

Page content applies to build 13.0.1.1071
