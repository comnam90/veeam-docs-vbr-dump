---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_oracle_rman_before.html"
last_updated: "11/8/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create an application backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process computers that you plan to add to the application backup policy.
* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.

Application backup policies have the following limitations:

* One backup object (computer, database system, or database) can be added only to one application backup policy. Otherwise, the application backup policy will fail.
* You can create application backups in a Veeam backup repository. If you want to save backups in other target locations, you must configure backup job on the computer with Veeam Plug-In installed.
* After you start managing a Veeam Plug-In with Veeam Backup & Replication, data backup for the computer is performed by a backup policy configured in Veeam Backup & Replication. Veeam Plug-In running on the computer starts a new backup chain on a target location specified in the backup policy settings. You cannot continue the existing backup chain that was created by Veeam Plug-In operating in the standalone mode.
* Application backup policy does not support backup of databases in a mounted state. If Veeam Plug-In detects a database in the mounted state, the application backup policy will finish with an error.

* If your database resides on a Oracle Exadata Database Machine, you may need to adjust the memory limit (memlock) for Veeam Transport Service. Otherwise, the application backup policy will fail. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4518).


