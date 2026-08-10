---
title: "Veeam Data Cloud Storage Vaults"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vdc_vaults.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Veeam Data Cloud Storage Vaults


Veeam Data Cloud Vault storage is a folder in an immutable blob container in the Cool access tier where Veeam Backup for Microsoft Azure stores image-level backups of Azure VMs, backups of Azure SQL databases, backups of Cosmos DB for PostgreSQL and Cosmos DB for MongoDB accounts, and backup copies of virtual network configurations. For more information, see the Veeam Data Cloud User Guide, section [Veeam Data Cloud Vault](https://helpcenter.veeam.com/docs/vdc/userguide/vault.html).

To communicate with storage vaults in Veeam Data Cloud Vault, Veeam Backup for Microsoft Azure uses Veeam Data Mover — a service that runs on [worker instances](azure_worker_instances.md) and that is responsible for data processing and transfer. When a backup policy addresses a storage vault, Veeam Data Mover establishes a connection with the repository to enable data transfer. To learn how Veeam Backup for Microsoft Azure communicates with storage vaults, see [Managing Repositories](azure_repositories.md).

|  |
| --- |
| Important |
| Backup files are stored in storage vaults in the native Veeam format and cannot be modified manually or by 3rd party tools. |

Encryption on Vaults

For enhanced data security, Veeam Backup for Microsoft Azure allows you to enable encryption at the vault level. Veeam Backup for Microsoft Azure encrypts backup files stored in storage vaults as follows:

* Data at rest is encrypted using 256-bit AES keys.
* Data in transit is encrypted using the TLS 1.2/1.3 protocol.

To learn how to enable encryption at the vault level, configure the vault settings as described in section [Adding Storage Vaults Using Web UI](azure_repository_vdc_ui_encryption.md).

Limitations for Vaults

Before you start creating storage vaults, keep in mind the following limitations:

* To use a Veeam Data Cloud storage vault as a target location for backed-up data, you must [get access to Veeam Data Cloud Vault](https://helpcenter.veeam.com/docs/vdc/userguide/vault_obtain_product.html) and [connect your backup appliance to the necessary storage vault](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#assigning-storage-vaults-to-workloads) as described in the Veeam Data Cloud User Guide, section Veeam Data Cloud Vault.

Keep in mind that the Veeam account that you use to connect to Veeam Data Cloud Vault must be associated with the product subscription as described in section [Adding Storage Vaults Using Web UI](azure_repository_vdc_ui_settings.md#location).

* Since all Azure storage accounts where storage vaults reside are managed by Veeam, you cannot use the Veeam Backup for Microsoft Azure Web UI or Veeam Data Cloud Vault customer portal to configure settings for these accounts manually.

Page updated 2026-05-13

