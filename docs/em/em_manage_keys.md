---
title: "Managing Encryption Keys"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_manage_keys.html"
last_updated: "7/31/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager provides you with an alternative way for data encryption. It lets you decrypt the data if you have lost or forgotten the password used for data encryption or if a KMS server used for data encryption is not available. For more information on the concept, terms and procedures of data encryption, see the [Data Encryption](https://helpcenter.veeam.com/docs/vbr/userguide/data_encryption.html?ver=13) section of the Veeam Backup & Replication User Guide.

For encryption, Veeam Backup Enterprise Manager uses an Enterprise Manager keyset — a pair of matching keys:

* Public Enterprise Manager key encrypts storage keys on backup servers connected to Veeam Backup Enterprise Manager.
* Private Enterprise Manager key decrypts storage keys in case a password for encrypted backup or tape is lost.

To let Veeam Backup & Replication encrypt and decrypt data with Enterprise Manager keys, make sure Enterprise Manager keys are enabled in Veeam Backup Enterprise Manager.

To enable Enterprise Manager keys, do the following:

1. In Veeam Backup Enterprise Manager, open the Settings section of the Configuration view.
2. On the Key Management tab, select the Enable encryption password loss protection check box.
3. To save the changes, click Save.

During Veeam Backup Enterprise Manager installation, the setup automatically generates an Enterprise Manager keyset. You can perform the following operations with Enterprise Manager keysets using Enterprise Manager:

* [Generate a new Enterprise Manager keyset](em_generating_em_keys.md)
* [Activate an Enterprise Manager keyset](em_activate_em_keys.md)
* [Specify retention settings for an Enterprise Manager keyset](em_retention_for_em_keys.md)
* [Export and import an Enterprise Manager keyset](em_export_import_keys.md)
* [Delete an Enterprise Manager keyset](em_delete_em_keyset.md)

Page updated 7/31/2024

Page content applies to build 13.0.1.1071
