---
title: "Step 5. Specify Switchover Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_ir_multiple_tas_specify_switchover_settings.html"
last_updated: "2/20/2024"
product_version: "13.0.1.1071"
---

# Step 5. Specify Switchover Settings


At this step of the wizard, specify database switchover options.

To select a switchover option and start the instant recovery session, do the following:

1. At the Specify switchover type field, select one of the following switchover options:

* Auto: switchover is performed automatically after all database files are copied and synchronized.
* Manual: switchover is started manually by user at any time after all database files are copied and synchronized.

* Scheduled: switchover is performed at a specified date and time. Use the drop-down calendar to specify the date and time.

1. Click Recover.

After you click Recover, Veeam Explorer for Oracle starts publishing the database on the target server.

[![Specifying Switchover Type](images/instant_switchover_veor.webp)](images/instant_switchover_veor.webp "Specifying Switchover Type")


