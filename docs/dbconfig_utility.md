---
title: "Veeam Configuration Database Connection Utility"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/dbconfig_utility.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Veeam Configuration Database Connection Utility

In this article

Veeam Backup & Replication comes with the configuration database connection utility that allows you to manage connection settings for Veeam Backup & Replication, Veeam Backup Enterprise Manager and Microsoft Entra ID. Using this utility, you can:

* Connect to a different database on the same or another Microsoft SQL Server or PostgreSQL instance. If you specify a database that does not exist yet, it will be created on the selected server.
* Change authentication method for database connection. Possible methods are Microsoft Windows authentication and Microsoft SQL Server or PostgreSQL native authentication.

This section of the guide explains how to manage database connection settings for Veeam Backup & Replication. If you want to manage database connection settings for Veeam Backup Enterprise Manager and Microsoft Entra ID, see [Veeam Backup Enterprise Manager Guide](https://helpcenter.veeam.com/docs/vbr/em/dbconfig_utility.html?ver=13) and [User Guide for Microsoft Entra ID](https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_connect_remote_repo.html?ver=13).

|  |
| --- |
| Note |
| Consider the following:   * The configuration database connection utility supports only connection to configuration databases of the current version. * The configuration database connection utility is shared between Veeam Backup & Replication and Veeam Backup Enterprise Manager. If they are installed on the same machine, make sure these products are of the same version. |

Related Topics

[Using Veeam Configuration Database Connection Utility](dbconfig_utility_linux.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
