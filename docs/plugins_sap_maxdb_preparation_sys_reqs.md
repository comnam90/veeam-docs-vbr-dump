---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_preparation_sys_reqs.html"
last_updated: "3/19/2026"
product_version: "13.0.1.2067"
---

# System Requirements


Before you start using Veeam Plug-In for SAP MaxDB, make sure the following requirements are met.

System Requirement

| Specification | Requirement |
| OS | Veeam Plug-In for SAP MaxDB is supported for the following x86\_64 versions of Linux distributions:   * RHEL 8.4 – 9.x  * SLES 15 SP3   Veeam Plug-In for SAP MaxDB is supported for the following Unix versions: IBM AIX 7.2 and 7.3 |
| Software | The protected computer must have FUSE libraries installed:   * [For SLES] libfuse2 * [For RHEL] fuse-libs |
| SAP MaxDB | Veeam Plug-In for SAP MaxDB supports SAP MaxDB 7.9.11. |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports management of Veeam Plug-In for SAP MaxDB 13. |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway.  For communication between the Veeam backup infrastructure and servers that host databases to be backed up, one of the following authentication protocols is required:   * Kerberos. To learn more, see [Kerberos Authenticationkerberos\_authentication](kerberos_authentication.md).   Keep in mind that Veeam Plug-In running on the Unix OS does not support Kerberos authentication.   * Windows New Technology LAN Manager (NTLM).   As NTLM is provided by Microsoft, only the Veeam backup server running on the Microsoft Windows OS supports NTLM.  If you have Veeam Plug-In running on the Unix OS and want to authenticate to a Veeam backup server running on Linux (Veeam Software Appliance), you cannot use domain accounts. In this case, you must use a local user account. We recommend specifying credentials for a local user account with the Service Account role. To learn more about available local user roles, see the [Configuring Users](https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_users.html?ver=13) topic in the Veeam Backup & Replication User Guide. |


