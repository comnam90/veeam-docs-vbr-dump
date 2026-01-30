---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_microsoft_sql_server_before.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create an application backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process computers that you plan to add to the application backup policy.
* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.
* The user that you plan to use to connect to the SQL instance must have sysadmin server role

Application backup policies have the following limitations:

* One backup object (computer, SQL instance, or database) can be added only to one application backup policy. Otherwise, the application backup policy will fail.

* You can create application backups in a Veeam backup repository. If you want to save backups in other target locations, you must configure backup job on the computer with Veeam Plug-In installed.

* After you start managing a Veeam Plug-In with Veeam Backup & Replication, data backup for the computer is performed by a backup policy configured in Veeam Backup & Replication. Veeam Plug-In running on the computer starts a new backup chain on a target location specified in the backup policy settings. You cannot continue the existing backup chain that was created by Veeam Plug-In operating in the standalone mode.


