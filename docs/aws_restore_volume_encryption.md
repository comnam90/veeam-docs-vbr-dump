---
title: "Step 6. Enable Encryption"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_volume_encryption.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Enable Encryption


[This step applies only if you have selected the Restore to new location, or with different settings option at the Restore Mode step of the wizard]

At the Encryption step of the wizard, choose whether the restored EBS volumes will be encrypted with an AWS KMS key:

* If you do not want to encrypt the EBS volumes or want to apply the existing encryption scheme, select the Use original encryption scheme option.
* If you want to encrypt the EBS volumes, select the Restore as encrypted volumes option and choose the necessary KMS key from the Encryption key list.

For a KMS key to be displayed in the list of available encryption keys, it must be stored in the AWS Region selected at [step 5](aws_restore_volume_mode.md) of the wizard and the IAM role or user specified for the restore operation at [step 4](aws_restore_volume_account.md#roles) of the wizard must have permissions to access the key. For more information on KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html).

|  |
| --- |
| Tip |
| If the necessary KMS key is not displayed in the list, or if you want to use a KMS key from an AWS account other than the AWS account to which the specified IAM role belongs, you can select Add custom key ARN from the Encryption key drop-down list, and specify the amazon resource name (ARN) of the key in the Add Custom Key ARN window.  For the backup appliance to be able to encrypt the restored EBS volumes using the provided KMS key, either the IAM role or user specified for the restore operation, or the IAM role used to create the restore point selected at [step 2](aws_restore_volume_settings.md) of the wizard must have permissions to access the key. |

[![Restoring EBS Volumes](images/aws_restore_volume_encryption.webp)](images/aws_restore_volume_encryption.webp "Restoring EBS Volumes")

Page updated 2026-05-22

