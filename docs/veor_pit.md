---
title: "Publishing Latest or Point-in-Time State"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_pit.html"
last_updated: "12/9/2024"
product_version: "13.0.1.1071"
---

# Publishing Latest or Point-in-Time State

In this article

After you have published a standalone database or a Data Guard database to an Oracle server (as described in [Publishing to Specified Server](vep_ptsr.md)), you can quickly republish the database to the same server.

You can republish either of the following states:

* [The latest available state](veor_latest.md) — to publish data as of the latest state in the backup file.
* [A point-in-time state](veor_pit_state.md) — to publish data as of the selected point-in-time state. This option is available only if backups of Oracle archived logs exist. For more information, see [Required Job Settings](veo_bu_job_settings.md).

When you unpublish a database, both options remain available until you close the application so that you can quickly republish the database if required.

Page updated 12/9/2024

Page content applies to build 13.0.1.1071
