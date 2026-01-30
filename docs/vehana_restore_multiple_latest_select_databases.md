---
title: "Step 2. Select Databases"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_multiple_latest_select_databases.html"
last_updated: "8/18/2025"
product_version: "13.0.1.1071"
---

# Step 2. Select Databases


At this step of the wizard, select the databases that you want to recover.

To quickly find the necessary databases, use the search field or sort the databases by name.

|  |
| --- |
| Note |
| The system database cannot be added to restore operations containing multiple databases. This is because you cannot simultaneously restore the system database of an SAP HANA system and its tenant databases — the SAP HANA system must be offline before you can restore the system database, while tenant databases require the system to be online during restore. |

[![Selecting Databases to Restore](images/vehana_multiple_restore_latest_select_databases.webp)](images/vehana_multiple_restore_latest_select_databases.webp "Selecting Databases to Restore")


