---
title: "Step 8. Specify SYSTEM User Password"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_single_tas_specify_password.html"
last_updated: "8/18/2025"
product_version: "13.0.1.1071"
---

# Step 8. Specify SYSTEM User Password

In this article

This step of the wizard is only available when the target server does not contain a database with the name you specified at the [Specify Database Name](vehana_restore_single_tas_specify_db_name.md) step. In this case, the SAP HANA system creates a new tenant database on the target server and a new SYSTEM user for the tenant database.

At this step, specify a password for this new SYSTEM user and click Restore.

The password policy follows the default SAP HANA configuration — the password must contain at least 8 characters, one uppercase, one lowercase letter, and one number.

[![Specifying System Password](images/vehana_specify_password.webp)](images/vehana_specify_password.webp "Specifying System Password")

Page updated 8/18/2025

Page content applies to build 13.0.1.1071
