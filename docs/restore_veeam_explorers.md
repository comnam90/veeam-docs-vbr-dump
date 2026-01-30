---
title: "Application Item Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_veeam_explorers.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# Application Item Restore


Veeam Backup & Replication provides additional tools called Veeam Explorers, that help you restore application items. Veeam Explorers are included in Veeam Backup & Replication installations, so you do not need to install them separately. You also do not need to purchase any additional license to use Veeam Explorers. For general information, see [Veeam Explorers Overview](explorers_introduction.md).

Veeam Explorers can restore application items from backups created with built-in application-aware processing provided by Veeam Backup & Replication or with database-level backups created by Veeam Plug-ins or MongoDB backup. For more information about the specifics of the options and which workloads they support, see [Databases and Enterprise Applications](protect_applications.md).

From image-based backups created with application-aware processing, you can restore items from the following applications:

* Microsoft Active Directory
* Microsoft SQL Server
* Oracle
* PostgreSQL
* Microsoft Exchange
* Microsoft SharePoint

|  |
| --- |
| Note |
| Application item restore for Microsoft OneDrive for Business and Microsoft Teams is supported for backups created by Veeam Backup for Microsoft 365. To restore data with Veeam Explorer for OneDrive for Business and Veeam Explorer for Microsoft Teams that come with Veeam Backup & Replication installations, you must add a Microsoft 365 database, a Veeam Backup for Microsoft 365 backup server or Veeam Backup for Microsoft 365 service provider. |

For more information, see [Launching Veeam Explorer from Image-Level Backups](restoring_veeam_explorers.md).

From database-level backups created by Veeam Plug-ins or MongoDB backup, you can restore items from the following applications:

* MongoDB
* SAP HANA
* Microsoft SQL Server
* Oracle

For more information, see [Launching Veeam Explorer from Plug-in or MongoDB Backup](launching_veeam_explorers_plugin.md).


