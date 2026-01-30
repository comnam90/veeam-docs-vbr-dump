---
title: "Publishing Latest or Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_publishing_latest_or_pit.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Publishing Latest or Point-in-Time State


After you have launched a publishing operation to a Microsoft SQL Server (as described in [Publishing to Specified Server](vesql_publishing_databases.md)), you can quickly republish a state of the database to the same server.

You can republish either of the following states:

* [The latest available state](vesql_publish_latest.md) — to publish data as of the latest state in the backup file.
* [A point-in-time state](vesql_publish_pit.md) — to publish data as of the selected point-in-time state. This option is available only if backups of Microsoft SQL Server transaction logs exist. For more information, see [Required Job Settings](vesql_bu_job_settings.md).

When you unpublish a database, both options remain available until you close the application so that you can quickly republish the database if required.


