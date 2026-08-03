---
title: "Performing Configuration Backup and Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_config_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Configuration Backup and Restore


You can back up and restore the appliance configuration database that stores data collected from the backup appliance for the existing backup policies, protected AWS resources, created worker instance configurations and profiles, added IAM roles and users, logged session records and so on. If the backup appliance goes down for some reason, you can reinstall it and quickly restore its configuration from a backup. You can also use a configuration backup to migrate the configuration of one backup appliance to another backup appliance in AWS.

It is recommended that you regularly perform configuration backup for every backup appliance present in AWS. Periodic configuration backups reduce the risk of data loss and minimize the administrative overhead costs in case any problems with the backup appliances occur.

You can run configuration backup manually on demand, or instruct the backup appliance to do it automatically on a regular basis.

In This Section

* [Performing Configuration Backup](aws_perform_config_backup.md)
* [Performing Configuration Restore](aws_perform_config_restore.md)

Page updated 2026-07-09

