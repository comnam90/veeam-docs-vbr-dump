---
title: "Microsoft Azure Data Lake"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_data_lake_add.html"
last_updated: "1/12/2026"
product_version: "13.0.1.1071"
---

# Microsoft Azure Data Lake

In this article

Before you add a Microsoft Azure Data Lake storage to the inventory of the virtual infrastructure, consider the following:

* Veeam Backup & Replication does not support backup from and restore to Veeam Data Cloud Vault.
* Veeam Backup & Replication does not support backup from and restore to the following types of Azure Blob Storage: Azure Data Box Storage, Azure Stack Edge.
* If you plan to use dedicated proxy servers, make sure these components are added in the [Backup Infrastructure](unstructured_data_backup_infrastructure.md).

To add a Microsoft Azure Data Lake storage as a source of unstructured data, do the following:

1. [Launch the New Object Storage wizard.](os_data_lake_launch.md)
2. [Specify account settings.](os_data_lake_account.md)
3. [Specify object storage processing settings.](os_data_lake_processing.md)
4. [Apply object storage settings.](os_data_lake_settings.md)
5. [Finish working with the wizard.](os_data_lake_finish.md)

Page updated 1/12/2026

Page content applies to build 13.0.1.1071
