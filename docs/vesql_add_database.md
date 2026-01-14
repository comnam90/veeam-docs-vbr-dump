---
title: "Adding Standalone Databases"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_add_database.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Adding Standalone Databases

In this article

|  |
| --- |
| Note |
| Before you add a standalone Microsoft SQL database, you must configure a staging SQL server. For more information, see [Configuring Staging SQL Server](vesql_configure_staging.md). |

To add a standalone Microsoft SQL database manually, do the following:

1. On the Home tab, click Add Database.

[![Adding Standalone Databases](images/new_database.webp)](images/new_database.webp "Adding Standalone Databases")

1. Specify the location of a primary database file, a secondary database file and associated log files. If necessary, specify the BLOB store location.

Manually added databases will be displayed in the navigation pane under the Other SQL Server Databases node.

[![Adding Microsoft SQL Databases Manually](images/vesql_external_database.webp)](images/vesql_external_database.webp "Adding Microsoft SQL Databases Manually")

Page updated 8/25/2025

Page content applies to build 13.0.1.1071
