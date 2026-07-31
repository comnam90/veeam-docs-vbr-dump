---
title: "Step 4. Specify PostgreSQL Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restore_databases_single_tas_specify_postgresql_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify PostgreSQL Settings


At this step of the wizard, specify the following PostgreSQL settings:

1. Specify a location to which you want to restore the PostgreSQL instance:

* Select Restore to the original location to restore the PostgreSQL instance to the original data directory.
* Select Restore to a different location to restore the PostgreSQL instance to a different location.

If you selected Restore to a different location, in the Instance port field, specify an instance port, which will also serve as an instance identifier. The port must be free.

![Step 4. Specify PostgreSQL Settings](images/vep_restore_to_another_server_postgresql_settings_database.webp "Specifying PostgreSQL Settings")

Page updated 2026-07-29

