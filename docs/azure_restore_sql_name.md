---
title: "Step 5. Specify SQL Database Name"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_restore_sql_name.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 5. Specify SQL Database Name


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Name step of the wizard, specify a new name for the restored Azure SQL database. It is recommended that you choose the new name carefully — due to Microsoft Azure limitations, you will not be able to rename the database after the restore operation completes.

|  |
| --- |
| Tip |
| You can specify a single prefix or suffix and add it to the names of multiple SQL databases. To do that, select the necessary SQL databases and click Name. In the Change Name window, select the Add prefix or Add suffix check box, and provide the text that you want to add. Then, click OK. |

[![Restore to Microsoft Azure SQL - Name](images/azure_restore_sql_name.webp)](images/azure_restore_sql_name.webp "Restore to Microsoft Azure SQL - Name")

Page updated 2025-08-26

