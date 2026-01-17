---
title: "Copying Data to Cloud Repositories"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/copy_to_cloud.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---


In this article

If you want to store copies of backups exported from Veeam Kasten in cloud repositories, you can connect to a service provider (SP) and store copies of these backups in cloud repositories. For more information, see the see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120).

To copy backups exported from Veeam Kasten to cloud repositories, do the following:

1. Depending on your environment, configure one of the following Cloud Connect Infrastructure types:

* [For service providers] Follow the steps described in the [Setting Up SP Veeam Cloud Connect Infrastructure](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_configure.html?ver=120) section in the Veeam Cloud Connect User Guide.
* [For tenants] Follow the steps described in the [Setting Up Tenant Veeam Cloud Connect Infrastructure](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_user_configure.html?ver=120) section in the Veeam Cloud Connect User Guide.

1. Run a Veeam Kasten policy.
2. Configure a backup copy job for backups exported from Veeam Kasten. Follow the instructions provided in [Creating Backup Copy Jobs](backup_copy.md).

Page updated 6/18/2024

Page content applies to build 13.0.1.1071
