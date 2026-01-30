---
title: "Cloud Credentials Manager"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cloud_credentials.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---

# Cloud Credentials Manager


You can use the Cloud Credentials Manager to create and maintain a list of credentials records that you plan to use to connect to cloud services.

|  |
| --- |
| Important |
| Veeam Backup & Replication 13.0.0 (build 13.0.0.4967) does not support backup to Veeam Cloud Connect. |

The Cloud Credentials Manager lets you create the following types of credentials records:

* [Veeam Cloud Connect Accounts](cloud_credentials_tenant.md)
* [Access Keys for AWS Users](cloud_credentials_aws.md)
* [Microsoft Azure Storage Accounts (Shared Key)](cloud_credentials_azure_storage.md)
* [Microsoft Azure Compute Accounts](restore_azure_accounts.md)
* [Microsoft Azure Storage Accounts (Entra ID)](azure_entra_id.md)
* [Google Cloud Accounts](cloud_credentials_google.md)
* [Google Cloud Service Accounts](cloud_credentials_gcp.md)

Credentials stored in the configuration database are encrypted with specific data protection mechanisms. For more information, see [How Database Data Encryption Works](encryption_database_hiw.md).

Related Topics

[Editing and Deleting Credentials Records](cloud_credentials_edit_delete.md)


