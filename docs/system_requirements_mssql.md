---
title: "System Requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_mssql.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# System Requirements

In this article

Before you start using Veeam Plug-In for Microsoft SQL Server, make sure the requirements listed in this section are met.

| Specification | Requirement |
| --- | --- |
| OS | 64-bit versions of the following operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   Note:  Server Core installations of Microsoft Windows Server OSes are not supported. |
| Microsoft SQL Server | The following Microsoft SQL Server versions are supported:   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016 * Microsoft SQL Server 2014 SP3   To connect to the Microsoft SQL Server, Veeam Plug-In requires Microsoft ODBC Driver for SQL Server versions 17 or 18. Other driver versions are not supported but can be present in the same system.  By default, Veeam Plug-In uses driver version 17. If driver version 17 is unavailable in the system, Veeam Plug-In automatically uses driver version 18. Optionally, you can manually set a preferred driver version in the veeam\_config.xml file for cases when the default driver version is not suitable for your system.  For details, see [Specifying the Version of Microsoft ODBC Driver for SQL Server](mssql_odbc_driver.md#driver).  Notes:   * Standard, Enterprise, Web, Developer editions of Microsoft SQL Server are supported. Express edition of Microsoft SQL Server is not supported. * Windows Server Failover Clusters are supported, both with shared disks and Cluster Shared Volumes (CSV). * Always On Availability Groups, Always On Clusterless Availability Groups and Always On Failover Cluster Instances are supported. Distributed Availability Groups are not supported. |
| Microsoft SQL Server Management Studio | Veeam Plug-In Toolbar requires Microsoft SQL Server Management Studio 21.  Note: Remote connections from Microsoft SQL Server Management Studio are not supported. |
| Veeam Backup & Replication | Veeam Backup & Replication 13 supports different on versions of Veeam Plug-In depending on which OS is running on the backup server:   * Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported. * Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.   Keep in mind that if you use an earlier Veeam Plug-In build than the one that is included in the installation ISO file of your Veeam Backup & Replication version, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474). |
| Network | Veeam Plug-In should be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway. |

Page updated 12/19/2025

Page content applies to build 13.0.1.1071
