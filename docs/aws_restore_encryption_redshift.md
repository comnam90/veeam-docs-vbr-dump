---
title: "Step 5. Enable Encryption"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_encryption_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Enable Encryption


[This step applies only if you have selected the Restore to original location with different settings option at the Restore Mode step of the wizard]

At the Encryption step of the wizard, choose whether the restored Redshift cluster will be encrypted with an AWS KMS key:

* If you want to apply the existing encryption scheme, select the Use original encryption scheme option.
* If you want to encrypt the Redshift cluster or want to change the key that is used for cluster encryption, select the Restore as encrypted instance option and choose the necessary key from the Encryption key drop-down list.

For a KMS key to be displayed in the list of available encryption keys, it must be stored in the AWS Region where the source Redshift cluster resides, and the IAM role or user specified for the restore operation at [step 3](aws_restore_account_redshift.md) of the wizard must have permissions to access the key. For more information on KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html).

|  |
| --- |
| Tip |
| If the necessary KMS key is not displayed in the list, or if you want to use a KMS key from an AWS account other than the AWS account to which the specified IAM role belongs, you can select Add custom key ARN from the Encryption key drop-down list, and specify the Amazon resource name (ARN) of the key in the Add Custom Key ARN window.  For the backup appliance to be able to encrypt the restored cluster using the provided KMS key, either the IAM role (or user) specified for the restore operation or the IAM role used to create the restore point that was selected at [step 2](aws_restore_point_redshift.md) of the wizard must have permissions to access the key. |

[![Restoring Redshift Clusters](images/aws_restore_encryption_redshift.webp)](images/aws_restore_encryption_redshift.webp "Restoring Redshift Clusters")

Page updated 2026-05-22

