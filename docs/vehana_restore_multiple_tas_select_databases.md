---
title: "Step 2. Select Databases"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_multiple_tas_select_databases.html"
last_updated: "12/6/2023"
product_version: "13.0.1.1071"
---

# Step 2. Select Databases

In this article

At this step of the wizard, select the databases that you want to recover.

To quickly find the necessary databases, use the search field or sort the databases by name.

|  |
| --- |
| Note |
| You can only select tenant databases in this window, for the following reasons:   * Restore of the system database to another server is not supported. * The system database cannot be restored simultaneously with tenant databases — the SAP HANA system must be offline before you can restore the system database, while tenant databases require the system to be online during restore. |

[![Selecting Databases to Restore](images/vehana_multiple_restore_latest_select_databases.webp)](images/vehana_multiple_restore_latest_select_databases.webp "Selecting Databases to Restore")

Page updated 12/6/2023

Page content applies to build 13.0.1.1071
