---
title: "Supported Applications"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_supported_platforms.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# Supported Applications

In this article

Veeam Agent for Microsoft Windows

You can use Veeam Agent for Microsoft Windows operating in the managed mode to create transactionally consistent backups of servers running applications that support Microsoft VSS. System requirements for VSS-aware processing are listed in the following table.

| Specification | Requirements and Limitations |
| --- | --- |
| Microsoft Active Directory Domain Controllers | The following versions of Microsoft Active Directory Domain Services servers (domain controllers) are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2 — if you use Veeam Backup & Replication on Microsoft Windows   Minimum supported domain and forest functional level is Microsoft Windows Server 2003. |
| Microsoft Exchange | The following versions of Microsoft Exchange are supported:   * Microsoft Exchange Subscription Edition * Microsoft Exchange 2019 * Microsoft Exchange 2016 |
| Microsoft SharePoint | The following versions of Microsoft SharePoint Server are supported:   * Microsoft SharePoint Server Subscription Edition * Microsoft SharePoint Server 2019 * Microsoft SharePoint Server 2016   All editions are supported (Foundation, Standard, Enterprise). |
| Microsoft SQL Server | The following versions of Microsoft SQL Server are supported:   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016 SP2 * Microsoft SQL Server 2014 SP3 * Microsoft SQL Server 2012 SP4   All editions of Microsoft SQL Server except LocalDB are supported. |
| Oracle | Oracle Database versions 11g to 21c are supported for the following operating systems (64-bit architecture):   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2 — if you use Veeam Backup & Replication on Microsoft Windows   For information about OS requirements for particular Oracle Database versions, see [Oracle documentation](https://docs.oracle.com/en/database/oracle/oracle-database/index.html).  IMPORTANT!   * Automatic Storage Management (ASM) is not supported. * Oracle Real Application Clusters (RAC) are not supported.  * Oracle Database systems running on Microsoft Windows Failover Clusters are not supported.  * Oracle servers using Data Guard are not supported. * Oracle Database Express Edition is supported. * 32-bit Oracle running on 64-bit operating systems is not supported. |

Veeam Agent for Linux

You can use Veeam Agent for Linux operating in the managed mode to create transactionally consistent backups of servers running Oracle, MySQL, and PostgreSQL database systems. For information on the limitations of data base processing, see [Backup of Database Systems](agents_backup_linux_dbs_processing.md#limitations). System requirements for database processing are listed in the following table.

| Specification | Requirements and Limitations |
| --- | --- |
| Oracle | * Oracle Database versions 11g to 21c are supported for all [operating systems supported by Veeam Agent for Linux](agents_system_requirements_linux.md#OS). * Automatic Storage Management (ASM) is not supported. * Oracle Real Application Clusters (RAC) are not supported. * Oracle Grid Infrastructure is not supported.  * Oracle Database Express Edition is not supported. * SAP on Oracle is not supported. * Oracle Database architectures with Data Guard and passive instances are not supported. |
| MySQL | * MySQL database system versions 5.7 to 9.0 are supported. * Configurations with multiple MySQL installations or instances on the same machine are not supported. * MySQL Cluster versions are not supported. |
| PostgreSQL | * PostgreSQL database system versions 13 – 17 are supported. * PostgreSQL clusters are not supported. |

Page updated 11/12/2025

Page content applies to build 13.0.1.1071
