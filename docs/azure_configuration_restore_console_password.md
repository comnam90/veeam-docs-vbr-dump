---
title: "Step 4. Specify Password"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration_restore_console_password.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 4. Specify Password


At the Password step of the wizard, specify the password used to encrypt the configuration backup file.

If you do not remember the password, you can restore configuration data without providing it. To do that, click the I forgot the password link and follow the instructions provided in [Decrypting Data Without Password](decrypt_without_pass.md).

|  |
| --- |
| Note |
| To restore configuration data without a password, the following requirements must be met:   * You must have either the Veeam Universal License or a legacy socket-based license (Enterprise edition or higher) installed on the backup server.  * The backup server must be connected to Veeam Backup Enterprise Manager, and password loss protection must be enabled on the Veeam Backup Enterprise Manager side for the duration of both the backup and restore operations. For more information, see the [Veeam Backup Enterprise Manager Guide](https://helpcenter.veeam.com/docs/backup/em/em_manage_keys.html?ver=120). |

![Step 4. Specify Password](images/azure_restore_config_pswd.webp)

Page updated 2025-08-19

