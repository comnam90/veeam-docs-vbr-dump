---
title: "Overview"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_managed_overview.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Overview

In this article

Veeam Backup & Replication offers the following management capabilities:

* Automated deployment and management of Veeam Plug-Ins. You can set up Veeam Backup & Replication to automatically discover computers that you want to protect with Veeam Plug-In for SAP HANA, Veeam Plug-In for Oracle RMAN, Veeam Plug-In for SAP on Oracle and Veeam Plug-In for Microsoft SQL Server, and deploy Veeam Plug-Ins on these computers. Once Veeam Plug-Ins are deployed on protected computers, you can use the Veeam Backup & Replication console to administrate Veeam Plug-Ins on multiple computers.
* Centralized configuration and management of backup policies on protected computers. You can use the Veeam Backup & Replication console to create and manage backup policies on computers in your infrastructure whose databases you want to protect. You can configure backup policies to apply settings on the computer, database system, or database level.
* Centralized backup jobs statistics and monitoring. You can use the Veeam Backup & Replication console to review reports about backup policies performance on computers in your infrastructure whose databases you want to protect.
* Centralized management of backups created by backup policies. If you choose to create backups on a backup repository managed by the Veeam backup server, you can use the Veeam Backup & Replication console to manage these backups.
* Secure database restore with recovery tokens. If you want to restore database from the backup and you are not the owner of this backup, you can ask your Backup Administrator to generate a recovery token. Using this recovery token, you can get access to a certain backup on the Veeam backup repository and restore database from this backup.

In This Section

* [Veeam Plug-In Management Infrastructure](management_infrastructure.md)
* [Computer Discovery and Veeam Plug-In Deployment](discovery_and_deployment.md)
* [Application Backup Policies](backup_policy.md)

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
