---
title: "Retention of Veeam Plug-In Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_managed_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retention of Veeam Plug-In Backups


Every successful application backup policy session creates a new restore point that lets you roll back database data to an earlier point in time. To control the number of restore points stored in the backup repository, Veeam Backup & Replication provides retention policies. The retention policy defines how many restore points you want to retain on disk and, thus, how ‘far’ you can roll back. After the restore point becomes outdated, Veeam Backup & Replication applies the retention policy and removes the restore point. You can configure the following retention policies for backups created with Veeam Plug-Ins:

* [Short-term retention policy](plugins_managed_retention_short.md) — keeps the latest restore points for a limited number of days.
* [Long-term retention policy (GFS)](plugins_managed_retention_gfs.md) — keeps selected full backups for longer periods, such as weeks, months and years.

Page updated 2026-06-16

