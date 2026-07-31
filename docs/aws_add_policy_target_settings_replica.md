---
title: "Configuring Snapshot Replica Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_target_settings_replica.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Snapshot Replica Settings


If you want to replicate cloud-native snapshots to other AWS accounts or regions, do the following:

1. In the Replicas section of the Targets step of the wizard, set the Replicate snapshots toggle to On.
2. In the Replication settings window, configure the following mapping settings for each AWS Region where source instances reside:

1. Select a source AWS Region from the list and click Edit Region Mapping.
2. In the Edit Region Mapping window, specify the following settings:

1. From the Target account drop-down list, select an IAM role whose permissions will be used to replicate cloud-native snapshots. The selected IAM role must belong to the AWS account in which the cloud-native snapshots will reside.

For an IAM role to be displayed in the list of available roles, it must be added to the backup appliance with the Amazon EC2 Replication operation selected as described in section [Adding IAM Roles](aws_iam_roles_add.md).

1. From the Target region drop-down list, select a target AWS Region to which the backup appliance will replicate cloud-native snapshots.
2. If you want to encrypt the replicated cloud-native snapshots with an AWS KMS key, select the Enable encryption check box and choose the necessary KMS key from the Encryption key drop-down list. Then, use the Key usage drop-down list to choose whether you want to encrypt snapshots for all volumes or only snapshots of the encrypted volumes. Note that if the original EBS volumes are encrypted, you must enable encryption for replicated snapshots as well — otherwise, the replication process will fail to complete successfully.

For a KMS key to be displayed in the list of available encryption keys, it must be stored in the target AWS Region, and the IAM role specified for the replication operation must have permissions to access the key. For more information on KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html).

1. Click Save.

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| To configure mapping for all source AWS Regions at a time, click Set Mapping for All Regions and follow the instructions provided at [step 2b](#step2.b) of the wizard. |

[![Creating EC2 Backup Policy](images/aws_backup_add_replication_mapping.webp)](images/aws_backup_add_replication_mapping.webp "Creating EC2 Backup Policy")

Related Resources

[AWS Key Management Service concepts](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)

Page updated 2026-05-21

