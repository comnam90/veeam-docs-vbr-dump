---
title: "Connecting Enterprise Manager to Another Configuration Database"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/dbconfig_utility.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Connecting Enterprise Manager to Another Configuration Database


The Configuration Database Connection Settings utility allows you to manage connection settings for Veeam Backup Enterprise Manager and Veeam Backup & Replication configuration databases.

Using this utility, you can perform the following:

* Connect Enterprise Manager and Veeam Backup & Replication to a different database on the same or another server.
* Change authentication method for database connection. Possible options are Microsoft Windows authentication and database server authentication.

|  |
| --- |
| Note |
| * With the Configuration Database Connection Settings utility, you can connect Enterprise Manager (or Veeam Backup & Replication) to a configuration database of the same product version only. For example, you can connect Enterprise Manager 13.0 to a configuration database of version 13.0. * The Configuration Database Connection Settings utility is shared between Veeam Backup & Replication and Veeam Backup Enterprise Manager. If they are installed on the same machine, make sure these products are of the same version. |

To manage connection settings for the Enterprise Manager configuration database, take the following steps:

1. [Launch the utility](dbconfig_launch.md).
2. [Select a product](dbconfig_product.md).
3. [Specify database connection settings](dbconfig_connection_settings.md).
4. [Apply connection settings](dbconfig_apply.md).
5. [Finish working with the wizard](dbconfig_summary.md).


