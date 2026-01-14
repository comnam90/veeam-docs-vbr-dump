---
title: "Staging SQL Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_staging_microsoft_sql_server.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# Staging SQL Server

In this article

To perform Microsoft SharePoint items restore, Veeam Explorer for Microsoft SharePoint requires a Microsoft SQL server to be used as a staging system.

|  |
| --- |
| Note |
| Configuring the staging SQL server settings is only required to restore SharePoint data from the following sources:   * Backups created by Veeam Backup & Replication. * Microsoft SharePoint databases manually added to the application scope. For more information, see [Adding Microsoft SharePoint Databases](vesp_adding_sp_databases.md). |

The server you plan to use as a staging system must meet the following requirements:

* A staging system must have the same or a later version of Microsoft SQL Server than the machine that hosts restored Microsoft SharePoint databases.
* As a staging server, you can use any edition of Microsoft SQL Server, including the Express Edition. You can download the necessary edition from the [Microsoft Download Center](https://www.microsoft.com/en-us/download).

Note that databases that exceed 10 GB cannot be attached to the Microsoft SQL Server Express Edition due to Express Edition limitations. For more information, see the [Editions and supported features of SQL Server 2022](https://learn.microsoft.com/en-us/sql/sql-server/editions-and-components-of-sql-server-2022?view=sql-server-ver16) Microsoft article.

* A Microsoft SQL Server that is included in a Microsoft SQL Server Failover Cluster cannot be used as a staging system.
* Nodes participating in Always On Availability Groups are supported. However, you should not use Availability Group Listeners as staging servers.

Note that the available authentication options for the staging server depend on the domain configuration. Consider the following:

* If the SQL server belongs to an untrusted domain, connection will not be possible.
* If the SQL server belongs to a trusted domain, only the SQL Server authentication method is available.
* If both the SQL server and the machine running Veeam Explorer for Microsoft SharePoint belong to the same domain, then both Windows authentication and SQL Server authentication methods are possible.

If you want to use Windows authentication, complete the following steps to configure delegation settings:

1. In Active Directory Users and Computers, select the necessary staging SQL server.
2. Open the server properties and select the Delegation tab. Select Trust this computer for delegation to specified services only and Use any authentication protocol options for the cifs service on a computer with Veeam Explorer for Microsoft SharePoint.
3. Restart the staging SQL Server.
4. Select a domain user account that you want to use when connecting to the staging server and make sure the Account is sensitive and cannot be delegated check box is not selected.

Remote BLOB Stores Support

A BLOB store must be either included in the SharePoint backup created by Veeam Backup & Replication or Veeam Agent for Microsoft Windows (for automated discovery) or stored on a local machine running Veeam Explorer for Microsoft SharePoint (for manual discovery).

|  |
| --- |
| Important |
| RBS FILESTREAM is the only provider that is supported in the current version. |

Make sure the staging Microsoft SQL Server configuration meets the following requirements:

1. FILESTREAM is enabled on a database server. For more information, see the following articles:

* For SQL Server 2022 for Windows, see [this Microsoft article](https://msdn.microsoft.com/en-us/library/cc645923%28v%3Dsql.130%29.aspx).
* For SQL Server 2019 for Windows, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/relational-databases/blob/enable-and-configure-filestream?view=sql-server-ver15).
* For SQL Server 2017 for Windows, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/relational-databases/blob/enable-and-configure-filestream?view=sql-server-2017).
* For SQL Server 2016, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/relational-databases/blob/enable-and-configure-filestream?view=sql-server-2016).
* For SQL Server 2014, see [this Microsoft article](https://learn.microsoft.com/en-us/previous-versions/sql/2014/relational-databases/blob/enable-and-configure-filestream?view=sql-server-2014).
* For SQL Server 2012, see [this Microsoft article](http://msdn.microsoft.com/en-us/library/cc645923%28v%3Dsql.110%29.aspx).

1. RBS Client Library is installed on the database server.

For Microsoft SQL Server 2014 and later, the Remote Blob Store setup is included in the installation media. For other versions, you can use the Microsoft SQL Server Remote Blob Store installation package. For more information on how to install the package, see [this Microsoft article](https://docs.microsoft.com/en-us/sharepoint/administration/install-and-configure-rbs).

Page updated 11/12/2025

Page content applies to build 13.0.1.1071
