---
title: "Step 6. Specify Database Processing Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_oracle_rman_database_processing.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Step 6. Specify Database Processing Settings

In this article

At the Database Processing step of the wizard, specify database credentials and log processing settings:

1. In the Credentials list, select the object and click Edit.
2. Specify database credentials and log processing settings for the objects in the list:

* [Processing settings](policy_oracle_rman_database_processing_general.md)
* [Only for databases] [Pluggable database settings](policy_oracle_rman_database_processing_database.md)

In the Credentials list, Veeam Backup & Replication shows only those objects that you added to the backup scope at the Databases step of the wizard. If you added a protection group, but need to specify settings for an individual computer or database in this protection group, you can add such objects to the list. To learn more, see [Adding Objects from Backup Scope](#add).

Adding Objects from Backup Scope

To add individual computers or databases to the Credentials list:

1. Click Add.
2. In the Select Objects window, select one or more objects in the list and click OK. You can select any of the following objects:

* Computer
* Oracle home
* Oracle database

You can press and hold [Ctrl] to select multiple objects at once.

To quickly find the necessary object, use the search field at the bottom of the Select Objects window.

1. Enter the object name or a part of it in the search field.
2. Click the Start search button on the right or press [Enter].

![Step 6. Specify Database Processing Settings](images/policy_rman_database_settings.webp)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
