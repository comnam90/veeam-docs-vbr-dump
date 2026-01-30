---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_sap_oracle_before.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create an application backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process computers that you plan to add to the application backup policy.
* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.

* The saphostcrl (SAP Host Agent) utility must be installed in advance on computers with databases that you want to protect. With this utility, Veeam Plug-In gets the list of database instances. To learn more, see [Database Detection](rescan_job_db_detection.md).

Application backup policies have the following limitations:

* One backup object (computer, database system, or database) can be added only to one application backup policy. Otherwise, the application backup policy will fail.

* You can create application backups on a Veeam backup repository. If you want to save backups in other target locations, you must configure backup job on the computer side.
* After you start managing a Veeam Plug-In with Veeam Backup & Replication, data backup for the computer is performed by a backup policy configured in Veeam Backup & Replication. Veeam Plug-In running on the computer starts a new backup chain on a target location specified in the backup policy settings. You cannot continue the existing backup chain that was created by Veeam Plug-In operating in the standalone mode.
* Veeam Plug-In may not be able to detect SAP instances during the configuration if the Oracle Database and SAP central instance are running on different hosts. If you work with Veeam Plug-In in the managed mode, this configuration is not supported. If you work with Veeam Plug-In in the standalone operation mode, see [Configuring Plug-In for SAP on Oracle](configure_sap_orcl.md).

* An application backup policy cannot back up Oracle installations with SAP BR\*Tools user and password in secure storage. If you work with Veeam Plug-In in the managed mode, this configuration is not supported.


