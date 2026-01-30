---
title: "Step 4. Specify PostgreSQL Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_ir_single_tas_specify_postgresql_settings.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify PostgreSQL Settings


At this step of the wizard, specify the following PostgreSQL settings:

1. Specify a location to which you want to restore the PostgreSQL instance:

* Select Restore to the original location to restore the PostgreSQL instance to the original data directory.
* Select Restore to a different location and specify a path in the Data directory path field to restore the PostgreSQL instance to another directory. To locate a new directory, click Browse and select a folder you want to use.

1. In the Instance port field, specify a free instance port, which will also serve as an instance identifier.

|  |
| --- |
| Note |
| If the target data directory is not empty, you will be prompted to overwrite it before proceeding to the next step. |

[![Specifying Database Files Target Location](images/vep_ir_to_another_server_postgresql_settings.webp)](images/vep_ir_to_another_server_postgresql_settings.webp "Specifying Database Files Target Location")


