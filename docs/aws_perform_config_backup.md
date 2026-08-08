---
title: "Performing Configuration Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_perform_config_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Configuration Backup


During configuration backup, data from configuration database of an appliance is exported and saved to a backup file in a repository. The appliance configuration database contains the following information: existing backup policies, protected AWS resources, created worker instance configurations and profiles, added IAM roles and users, logged session records and so on.

|  |
| --- |
| Important |
| If your backup appliance is managed by a Veeam Backup & Replication server, you will neither be able to perform manual or scheduled configuration backup of the backup appliance from the Web UI, nor to export the configuration data from the Web UI. In this case, you can perform configuration backup using the Veeam Backup & Replication console as described in section [Performing Configuration Backup Using Console](aws_config_backup_console.md). |

In This Section

* [Performing Configuration Backup Using Console](aws_config_backup_console.md)
* [Performing Configuration Backup Using Web UI](aws_config_backup_ui.md)

Page updated 2026-05-21

