---
title: "Decrypting Tapes With Enterprise Manager Keys"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_decrypt_no_password.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Decrypting Tapes With Enterprise Manager Keys

In this article

If you have lost or forgotten a password or you cannot use KMS keys due to a KMS server failure, you can restore encrypted data using password loss protection provided by Veeam Backup Enterprise Manager. This solution allows you to include Enterprise Manager keyset in the encryption process and use it to decrypt tapes. For more information, see the [Enterprise Manager Keys](https://helpcenter.veeam.com/docs/backup/vsphere/enterprise_manager_keys.html) section in the Veeam Backup & Replication User Guide.

Password loss protection has the following requirements and limitations:

* To use password loss protection, you must have a paid license. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).
* Backup servers that you use for data decryption must be connected to the same instance of Veeam Backup Enterprise Manager. If you connect the backup server to several instances of Veeam Backup Enterprise Manager, this may cause unexpected behavior, and the decryption process may fail.
* Password loss protection must be enabled on Veeam Backup Enterprise Manager. For more details, see the [Managing Encryption Keys](https://helpcenter.veeam.com/docs/backup/em/em_manage_keys.html) section in the Veeam Backup Enterprise Manager Guide.

To decrypt backup files with Enterprise Manager keys, you need to issue a request to Veeam Backup Enterprise Manager using the following wizards:

* The Encryption Key Restore wizard on the backup server.
* The Password Recovery wizard on the Veeam Backup Enterprise Manager server.

To complete the operation, perform the following steps:

1. [Create a request for key restore](tape_restore_nopass.md).
2. [Process the request in Veeam Backup Enterprise Manager](tape_restore_nopass2.md).
3. [Complete the key restore process](tape_restore_nopass3.md).

Page updated 5/21/2025

Page content applies to build 13.0.1.1071
