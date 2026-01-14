---
title: "Adding Veeam Backup for Microsoft 365 Databases"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veod_adding_vbo_databases_od.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# Adding Veeam Backup for Microsoft 365 Databases

In this article

To manually add databases that store Microsoft 365 organization data, do the following:

1. Do one of the following:

* On the Home tab, click Add Org > Veeam Backup for Microsoft 365 database on the ribbon.
* Right-click the Organizations node and select Veeam Backup for Microsoft 365 database.

1. Specify the database file location and log directory.

1. Click Open.

[![Adding Veaam Backup for Microsoft 365 Databases](images/adding_adb_2.webp)](images/adding_adb_2.webp "Adding Veaam Backup for Microsoft 365 Databases")

|  |
| --- |
| Note |
| Make sure you have disabled the Veeam Backup Proxy for Microsoft 365 Service when adding local databases. You can stop this service by using the services.msc console. If you try to add a database having this service still in progress, you will receive an error message and will not be able to access the database due to database lock. |

Page updated 10/6/2025

Page content applies to build 13.0.1.1071
