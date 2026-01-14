---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_backup_copy_create_prerequisites.html"
last_updated: "10/31/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a backup copy job, check the prerequisites and limitations:

* Backup infrastructure components that will take part in the backup copy process must be added to the backup infrastructure and properly configured. These include source and target backup repositories between which backups must be copied.
* The target backup repository must have enough free space to store copied backups. To receive alerts about low space on the backup repository, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).

* For Veeam Plug-In backup copy jobs, you cannot select the [Veeam Cloud Connect repository](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_configure_repository.html?ver=13) as a backup copy target.

Page updated 10/31/2025

Page content applies to build 13.0.1.1071
