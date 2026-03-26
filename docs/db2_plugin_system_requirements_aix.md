---
title: "System Requirements for IBM AIX"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_plugin_system_requirements_aix.html"
last_updated: "3/19/2026"
product_version: "13.0.1.2067"
---

# System Requirements for IBM AIX


Before you start using Veeam Plug-In for IBM Db2 on machines running IBM AIX, make sure the requirements listed in this section are met.

System Requirements for IBM AIX

| Specification | Requirement |
| OS | Veeam Plug-In is supported for the following Unix versions:   * IBM AIX 6: 6.1 * IBM AIX 7: 7.1, 7.2, 7.3   For additional information about supported IBM AIX versions that are listed for supported configurations of IBM Db2, see [this IBM article](https://www.ibm.com/support/pages/system-requirements-ibm-db2-linux-unix-and-windows). |
| IBM Db2 | Veeam Plug-In for IBM Db2 supports the following configurations of IBM Db2:   * Versions: 10.5, 11.1, 11.5 and 12.1 * Editions: Standard, Advanced * Environments: standalone servers, high availability disaster recovery (HADR), failover clusters   In case of HADR and failover clusters, Veeam Plug-In supports the following cluster management software: TSA, Pacemaker for Linux OSes, PowerHA for IBM AIX. |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports different on versions of Veeam Plug-In depending on which OS is running on the backup server:   * Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported. * Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.   Keep in mind that if you use an earlier Veeam Plug-In build than the one that is included in the installation ISO file of your Veeam Backup & Replication version, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474). |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway.  For communication between the Veeam backup infrastructure and servers that host databases to be backed up, one of the following authentication protocols is required:   * Kerberos. To learn more, see [Kerberos Authenticationkerberos\_authentication](kerberos_authentication.md).   Keep in mind that Veeam Plug-In running on the Unix OS does not support Kerberos authentication.   * Windows New Technology LAN Manager (NTLM).   As NTLM is provided by Microsoft, only the Veeam backup server running on the Microsoft Windows OS supports NTLM.  If you have Veeam Plug-In running on the Unix OS and want to authenticate to a Veeam backup server running on Linux (Veeam Software Appliance), you cannot use domain accounts. In this case, you must use a local user account. We recommend specifying credentials for a local user account with the Service Account role. To learn more about available local user roles, see the [Configuring Users](https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_users.html?ver=13) topic in the Veeam Backup & Replication User Guide. |


