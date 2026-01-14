---
title: "Password Loss Protection"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encryption_password_loss_protection.html"
last_updated: "11/20/2024"
product_version: "13.0.1.1071"
---

# Password Loss Protection

In this article

If you have lost or forgotten a password or you cannot use KMS keys due to a KMS server failure, you can restore encrypted data using password loss protection provided by Veeam Backup Enterprise Manager. This solution allows you to include Enterprise Manager keyset in the encryption process and use it to decrypt backup files. For more information, see [Enterprise Manager Keys](enterprise_manager_keys.md).

Password loss protection has the following requirements and limitations:

* To use password loss protection, you must have a paid license. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).
* Backup servers that you use for data decryption must be connected to the same instance of Veeam Backup Enterprise Manager. If you connect the backup server to several instances of Veeam Backup Enterprise Manager, this may cause unexpected behavior, and the decryption process may fail.

* Password loss protection must be enabled on Veeam Backup Enterprise Manager. For more details, see the [Managing Encryption Keys](https://helpcenter.veeam.com/docs/vbr/em/em_manage_keys.html?ver=13) section in the Veeam Backup Enterprise Manager Guide.

For more information on how to decrypt backups with Enterprise Manager keys, see [Decrypting Backups With Enterprise Manager Keys](decrypt_without_pass.md).

Page updated 11/20/2024

Page content applies to build 13.0.1.1071
