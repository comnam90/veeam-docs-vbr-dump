---
title: "Standalone and Managed Operations Modes"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/overview_operation_modes.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---

# Standalone and Managed Operations Modes

In this article

Depending on the available infrastructure, some Veeam Plug-Ins can operate in either of two modes to optimize database protection. Based on the operation mode, Veeam Plug-Ins have different functionality and limitations.

Standalone Mode

In this mode, you must manually install Veeam Plug-In that supports standalone mode directly on the computer whose databases you want to protect.

For Veeam Plug-Ins operating in the standalone mode, data protection, disaster recovery and administration tasks are performed by the user on the computer with Veeam Plug-In installed.

You can use Veeam Plug-In operating in the standalone mode with Veeam Backup & Replication. In this scenario, you can use backup repositories managed by Veeam Backup & Replication as a target location for backups and use the Veeam Backup & Replication console to perform a number of tasks with backup jobs and backups.

For details, see [Standalone Veeam Plug-Ins](protect_applications_standalone_vp.md).

Managed Mode

In this mode, you can automate management of solutions for enterprise applications on multiple computers in your infrastructure in the Veeam Backup & Replication console. You can configure application backup policies and jobs and perform other data protection and administration tasks on remote computers. To use solutions operating in the managed mode, you must install Veeam Backup & Replication on the Veeam backup server and deploy the Veeam components using the Veeam Backup & Replication console.

* For details about managed Veeam Plug-In deployment, see [Computer Discovery and Veeam Plug-In Deployment](discovery_and_deployment.md).
* For details about deployment of Veeam components for MongoDB Backup, see [Computer Discovery and Veeam Components Deployment](mongo_discovery_and_deployment.md).

For solutions managed by Veeam Backup & Replication, data protection, data restore and administration tasks are performed by a backup administrator in the Veeam Backup & Replication console:

* For details about managed Veeam Plug-Ins, see [Managed Veeam Plug-Ins](management.md).
* For details on how to back up MongoDB items, see [MongoDB Backup](mongo_backup.md).

Supported Operation Modes

The following table describes the support of operation modes by solutions for enterprise applications.

| Operation Mode | Veeam Plug-In for Oracle RMAN | Veeam Plug-In for SAP HANA | Veeam Plug-In for SAP on Oracle | Veeam Plug-In for SAP MaxDB | Veeam Plug-In for Microsoft SQL Server | Veeam Plug-In for IBM Db2 | MongoDB Backup |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Standalone mode | Supported | Supported | Supported | Supported | Supported | Supported | Not supported |
| Managed mode | Supported | Supported | Supported | Not supported | Supported | Not supported | Supported |

Page updated 11/5/2025

Page content applies to build 13.0.1.1071
