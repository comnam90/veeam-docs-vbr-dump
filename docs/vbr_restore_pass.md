---
title: "Step 5. Specify Password"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_restore_pass.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Step 5. Specify Password


The Password step of the wizard is available if you have enabled the encryption option in the configuration backup properties.

Enter the password to decrypt configuration backup data:

1. Check the password hint to recall the password.
2. In the Password field, enter the password to decrypt the configuration backup file.

If you forgot or lost the password, click the I forgot the password link. For more information, see [Decrypting Data Without Password](decrypt_without_pass.md).

|  |
| --- |
| Note |
| The availability of restoring configuration data without a password depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).  Also, your backup server must be connected to Veeam Backup Enterprise Manager. Otherwise, you will not see the I forgot the password link. |

![Step 5. Specify Password](images/vbr_restore_pass.webp)


