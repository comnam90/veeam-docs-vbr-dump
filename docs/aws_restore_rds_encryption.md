---
title: "Step 5. Enable Encryption"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds_encryption.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Enable Encryption


[This step applies only if you have selected the Restore to new location, or with different settings option at the Restore Mode step of the wizard]

At the Encryption step of the wizard, choose whether the restored RDS resources will be encrypted with an AWS KMS key:

* If you do not want to encrypt the RDS resources or want to apply the existing encryption scheme, select the Use original encryption scheme option.

|  |
| --- |
| Important |
| If you plan to restore an unencrypted Aurora provisioned DB cluster to an Aurora Serverless DB cluster, and you select the Use original encryption scheme option, note that the backup appliance will encrypt the newly created Aurora Serverless DB cluster with the default KMS key in the target AWS Region. For more information on Aurora Serverless, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-serverless.html). |

* If you want to encrypt the RDS resources, select the Restore as encrypted instance option and choose the necessary KMS key from the Encryption key list.

For a KMS key to be displayed in the list of available encryption keys, it must be stored in the AWS Region selected at [step 4](aws_restore_rds_mode.md) of the wizard and the IAM role or user specified for the restore operation at [step 3](aws_restore_rds_account.md) of the wizard must have permissions to access the key. For more information on KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html).

|  |
| --- |
| Tip |
| If the necessary KMS key is not displayed in the list, or if you want to use a KMS key from an AWS account other than the AWS account to which the specified IAM role belongs, you can select Add custom key ARN from the Encryption key drop-down list, and specify the amazon resource name (ARN) of the key in the Add Custom Key ARN window.  For the backup appliance to be able to encrypt the restored RDS resource using the provided KMS key, either the IAM role or user specified for the restore operation, or the IAM role used to create the restore point selected at [step 2](aws_restore_rds_point.md) of the wizard must have permissions to access the key. |

[![Restoring RDS Resources](images/aws_rds_restore_encryption.webp)](images/aws_rds_restore_encryption.webp "Restoring RDS Resources")

Page updated 2026-05-22

