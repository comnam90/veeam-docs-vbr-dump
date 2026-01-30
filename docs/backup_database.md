---
title: "Veeam Backup & Replication Configuration Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_database.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Veeam Backup & Replication Configuration Database


Veeam Backup & Replication Configuration Database stores data about the backup infrastructure, jobs, sessions and other configuration data. The database instance can be located on a Microsoft SQL Server or PostgreSQL installed either locally (on the same machine where the backup server is running) or remotely.

Veeam Backup & Replication maintains the configuration database. Veeam Backup & Replication runs the DatabaseMaintenance system job once a week and when the Veeam Backup Service is restarted. The job updates the database internal statistics, defragments indexes and clears unused data. For details, see the Job.DatabaseMaintenance.log file in the %ProgramData%\Veeam\Backup folder.

In This Section

[Managing Configuration Database](vbr_config.md)


