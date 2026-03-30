---
title: "Image-Level Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protect_applications_image.html"
last_updated: "3/27/2026"
product_version: "13.0.1.2067"
---

# Image-Level Backup


With the application-aware processing, Veeam Backup & Replication and Veeam Agent for Linux create image-level backups of your workload and also backs up application logs. To back up application logs, you must enable application-aware processing in the backup job settings. For more information, see guides or sections dedicated to your platform:

* For virtual machines, application-aware processing with Veeam Backup & Replication allows you to create image-level backups together with a transactionally-consistent backups of the following applications:

* Microsoft Exchange
* Microsoft SharePoint
* Microsoft SQL Server
* Oracle
* PostgreSQL

To learn more, see [Application-Aware Processing](application_aware_processing.md).

* For physical machines, application-aware processing with Veeam Agent for Linux allows you to create image-level backups together with a transactionally-consistent backups of the following applications:

* MySQL
* Oracle
* PostgreSQL

To learn more, see [Backup of Database Systems](agents_backup_linux_dbs_processing.md).

For recovery, Veeam Backup & Replication provides recovery of workloads themselves as well as recovery of application items. For recovery, Veeam Backup & Replication uses tools called Veeam Explorers. Veeam Explorers are distributed as part of Veeam Backup & Replication, and you do not need to install them separately. You also do not need to purchase any additional license to use Veeam Explorers. For information on how to launch Veeam Explorers to restore application items, see [Launching Veeam Explorer from Image-Level Backups](restoring_veeam_explorers.md). As an alternative, you can launch Veeam Explorers as a separate tool. For more information, see the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13).


