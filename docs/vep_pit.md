---
title: "Publishing Latest or Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_pit.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Publishing Latest or Point-in-Time State


After you have launched a publishing operation to a PostgreSQL instance (as described in [Publishing to Specified Server](vep_ptsr.md)), you can quickly republish a state of the PostgreSQL instance to the same server.

You can republish either of the following states:

* [The latest available state](vep_latest.md) — to publish data as of the latest state in the backup file.
* [A point-in-time state](vep_pit_state.md) — to publish data as of the selected point-in-time state. This option is available only if backups of PostgreSQL write ahead log (WAL) files exist. For more information, see [Required Job Settings](vep_bu_job_settings.md).

When you unpublish an instance, both options remain available until you close the application so that you can quickly republish the instance if required.


