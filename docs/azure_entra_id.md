---
title: "Microsoft Azure Storage Accounts (Entra ID)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_entra_id.html"
last_updated: "11/29/2024"
product_version: "13.0.1.1071"
---

# Microsoft Azure Storage Accounts (Entra ID)


You can create a credentials record for a Microsoft Azure Storage account with Microsoft Entra authorization to connect to the following types of accounts:

* Azure Blob Storage added as an [object storage repository](osr_adding_blob_storage.md), a [performance extent](backup_repository_sobr_extents.md) or [capacity extent](capacity_tier.md) of a scale-out backup repository. Use this option to store data on Azure Blob Storage.
* Azure Archive Storage added as an [archive extent](new_archive_tier.md) of a scale-out backup repository. Use this option to store data on Azure Blob Storage.
* Microsoft Azure Blob Storage [added as a source of unstructured data](os_azure_add.md). Use this option to backups data located on Azure Blob Storage repository and restore backed-up data.
* Veeam Data Cloud Vault added as an [object storage repository](osr_adding_blob_storage.md), a [performance extent](backup_repository_sobr_extents.md) or [capacity extent](capacity_tier.md) of a scale-out backup repository. Use this option to store data on Veeam Data Cloud Vault.

To add a Microsoft Azure storage account with Microsoft Entra authorization, use the Microsoft Azure Storage Account (Entra ID) wizard:

1. [Check prerequisites.](entraid_before_you_begin.md)
2. [Launch the Microsoft Azure Storage Account (Entra ID) wizard](entraid_launch.md).
3. [Specify the account name](entraid_name.md).
4. [Select account type](entraid_access.md).
5. [Specify authentication settings](entraid_access.md).
6. [Finish working with the wizard](entraid_finish.md).


