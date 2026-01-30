---
title: "Step 7. Specify Log Processing Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_microsoft_sql_server_log_processing.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Step 7. Specify Log Processing Settings


At the Log processing step of the wizard, specify credentials and log processing options for the added objects:

1. In the Objects list, select the object and click Edit.
2. Specify log processing settings for the objects in the list. To learn more, see [Processing settings](policy_microsoft_sql_server_processing_general.md).

In the Objects list, Veeam Backup & Replication shows only those objects that you added to the backup scope at the Databases step of the wizard. If you added a protection group, but need to specify settings for an individual computer or database in this protection group, you can add such objects to the list. To learn more, see [Adding Objects from Backup Scope](#add).

Adding Objects from Backup Scope

To add protection groups, individual computers or databases to the Objects list:

1. Click Add.
2. In the Select Objects window, select one or more objects in the list and click OK. You can select any of the following objects:

* Protection group
* Computer

* SQL instance

* SQL database

You can press and hold [Ctrl] to select multiple objects at once.

To quickly find the necessary object, use the search field at the bottom of the Select Objects window.

1. Enter the object name or a part of it in the search field.
2. Click the Start search button on the right or press [Enter].

![Step 7. Specify Log Processing Settings](images/plugins_policy_mssql_log_processing.webp)


