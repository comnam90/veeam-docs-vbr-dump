---
title: "Step 6. Specify SYSTEM User Password"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_multiple_pit_specify_password.html"
last_updated: "8/18/2025"
product_version: "13.0.1.1071"
---

# Step 6. Specify SYSTEM User Password


This step of the wizard is only available if any of the databases selected at the [Select Databases](vehana_restore_multiple_pit_select_databases.md) step do not exist on the target server. In this case, the SAP HANA system creates new tenant databases on the target server and a new SYSTEM user for the new databases.

At this step, specify a password for this new SYSTEM user and click Restore.

The password policy follows the default SAP HANA configuration — the password must contain at least 8 characters, one uppercase, one lowercase letter, and one number.

|  |
| --- |
| Note |
| This password applies to all databases created during the restore process. |

[![Specifying System Password](images/vehana_specify_password_multiple.webp)](images/vehana_specify_password_multiple.webp "Specifying System Password")


