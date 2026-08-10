---
title: "Step 5. Specify Database Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restore_databases_multiple_tas_specify_db_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Database Account


At this step of the wizard, specify a PostgreSQL account to use for authentication:

* Select Use Linux credentials to use the credentials of the Linux system user.
* Select System user without password (peer) to use peer authentication. With peer authentication, no password is required.
* Select Database user with password and specify the following:

1. In the Username field, enter the PostgreSQL user name.
2. In the Password field, enter the password for the specified user.

![Step 5. Specify Database Account](images/vep_restore_databases_account.webp "Specifying PostgreSQL Account")

Page updated 2026-04-17

