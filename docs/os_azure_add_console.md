---
title: "Adding Microsoft Azure Object Storage Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_azure_add_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Microsoft Azure Object Storage Using Console


Before you add a Microsoft Azure Blob storage to the inventory of the virtual infrastructure, consider the following:

* Veeam Backup & Replication does not support backup from and restore to Veeam Data Cloud Vault.
* Veeam Backup & Replication does not support backup from and restore to the following types of Azure Blob Storage: Azure Data Box Storage, Azure Stack Edge.
* If you plan to use dedicated proxy servers, make sure these components are added in the [Backup Infrastructure](unstructured_data_backup_infrastructure.md).

To add a Microsoft Azure Blob storage as a source of unstructured data, do the following:

1. [Launch the New Object Storage wizard](os_azure_launch.md).
2. [Specify account settings](os_azure_account.md).
3. [Specify object storage processing settings](os_azure_processing.md).
4. [Apply object storage settings](os_azure_apply.md).
5. [Finish working with the wizard](os_azure_finish.md).

Page updated 2026-07-24

