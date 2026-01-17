---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_systemreqs.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# System Requirements

In this article

The system requirements depend on whether you want to use an image-level backup created with native Veeam Backup & Replication functionality or an application backup created with Veeam Plug-In for Microsoft SQL Server.

Data Recovery from Image-Level Backups

This section lists system requirements that are relevant when recovering data from image-level backups created by Veeam Backup & Replication.

| Component | Requirement |
| --- | --- |
| Microsoft SQL Server | Veeam Explorer for Microsoft SQL Server supports restore of the following Microsoft SQL Server versions:   * Microsoft SQL Server 2025 (only for Windows) * Microsoft SQL Server 2022 (only for Windows) * Microsoft SQL Server 2019 (only for Windows) * Microsoft SQL Server 2017 (only for Windows) * Microsoft SQL Server 2016 SP2 * Microsoft SQL Server 2014 SP3 * Microsoft SQL Server 2012 SP4   All editions of Microsoft SQL Server except LocalDB are supported.  The database whose logs you want to back up must use the Full or Bulk-logged recovery model. In this case, all changes of the Microsoft SQL Server state will be written to transaction logs, and you will be able to replay transaction logs to restore the Microsoft SQL Server. You can use the Microsoft SQL Server Management Studio to switch to one of these models. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/recovery-models-sql-server?view=sql-server-2017).  Restore of Microsoft SQL Server data may require an available staging Microsoft SQL Server. To learn how to configure this server, see [Configuring Staging SQL Server](vesql_configure_staging.md). |

Consider the following:

* By default, the AUTO\_CLOSE option for Microsoft SQL Server databases is set to False.

If AUTO\_CLOSE is enabled, your databases may be skipped from processing.

* [For machines with ReFS] The mount server, target server, staging server, backup server and the machine where the Veeam Backup & Replication console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).

* Nodes participating in Always On Availability Groups are supported, but using Availability Group Listeners as staging servers is not recommended.

Staging SQL Server Requirements

Consider the following:

* Make sure that the staging server has the same version of Microsoft SQL Server as the source server, or a later version.
* As a staging server, you can use any edition of Microsoft SQL Server, including the Express Edition. You can download the necessary edition from the [Microsoft Download Center](https://www.microsoft.com/en-us/download).

Note that databases that exceed 10 GB cannot be attached to the Microsoft SQL Server Express Edition due to Express Edition limitations. For more information, see the [Editions and supported features of SQL Server 2022](https://learn.microsoft.com/en-us/sql/sql-server/editions-and-components-of-sql-server-2022?view=sql-server-ver16) Microsoft article.

* A SQL Server included in Microsoft SQL Server failover cluster cannot be used as a staging system.
* Configure domain trusts when planning to add databases to the Veeam Explorer for Microsoft SQL Server scope manually. For more information, see [Configuring Staging SQL Server](vesql_configure_staging.md).

Restore from SQL Plug-in Backups

This section lists system requirements that are relevant when restoring data from backups created with Veeam Plug-In for Microsoft SQL Server (in managed or standalone mode).

| Component | Requirement |
| --- | --- |
| Microsoft SQL Server | The following Microsoft SQL Server versions are supported:   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016 * Microsoft SQL Server 2014 SP3   To connect to the Microsoft SQL Server, Veeam Plug-In requires Microsoft ODBC Driver for SQL Server versions 17 or 18. Other driver versions are not supported but can be present in the same system.  By default, Veeam Plug-In uses driver version 17. If driver version 17 is unavailable in the system, Veeam Plug-In automatically uses driver version 18. Optionally, you can manually set a preferred driver version in the veeam\_config.xml file for cases when the default driver version is not suitable for your system.  For details, see [Specifying the Version of Microsoft ODBC Driver for SQL Server](mssql_odbc_driver.md).  Notes:   * Standard, Enterprise, Web, Developer editions of Microsoft SQL Server are supported. Express edition of Microsoft SQL Server is not supported. * Windows Server Failover Clusters are supported, both with shared disks and Cluster Shared Volumes (CSV). * Always On Availability Groups, Always On Clusterless Availability Groups and Always On Failover Cluster Instances are supported. Distributed Availability Groups are not supported. |

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
