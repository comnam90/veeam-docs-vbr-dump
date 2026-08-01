---
title: "Creating RDS Snapshots Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_snapshot_manual_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating RDS Snapshots Manually


Veeam Plug-in for AWS allows you to manually create snapshots of RDS resources. You can instruct the backup appliance to store the created snapshots in the same AWS Regions where the processed DB instances and DB clusters reside, or in a different AWS Region or AWS account.

|  |
| --- |
| Note |
| The backup appliance does not include snapshots created manually in the snapshot chain and does not apply the configured retention policy settings to these snapshots. This means that the snapshots are kept in your AWS environment unless you remove them manually, as described in section [Managing Backed-Up RDS Data](aws_backups_view_rds.md). |

To manually create a cloud-native snapshot of a DB instance or an Aurora DB cluster, do the following:

1. Navigate to Resources > Databases > RDS.
2. Select the necessary instance and click Take Snapshot Now.

For an RDS resource to be displayed in the list of available instances, an AWS Region where the instance resides must be added to any of [configured RDS backup policies](aws_add_policy_source_settings_rds.md), and the IAM role specified in the backup policy settings or in the organization settings must have permissions to access the instance. For more information on the required permissions, see [RDS Backup IAM Role Permissions](aws_role_permissions_backup_rds.md).

1. Complete the Take Manual Snapshot wizard:

1. At the Account step of the wizard, specify an IAM role whose permissions the backup appliance will use to create the snapshot. The specified IAM role must belong to the same AWS account to which the processed RDS resources reside.

For an IAM role to be displayed in the list of available roles, it must be added to the backup appliance as described in section [Adding IAM Roles](aws_iam_roles_add.md).

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support taking manual snapshot using IAM roles specified in the [organization settings](aws_organization_add_settings.md). |

1. At the Snapshot Mode step of the wizard, choose whether you want to store the snapshot in the same AWS Region where the processed RDS resource resides, or in another AWS Region or AWS account.
2. [Applies only if you have selected the New location option] At the Settings step of the wizard, do the following:

1. In the Replication settings section, choose the target AWS Region in which the snapshot will be stored and specify an IAM role whose permissions will be used to replicate the snapshot. The specified IAM role must belong to the AWS account to which you want to replicate the snapshot.

For an IAM role to be displayed in the list of available roles, it must be added to the backup appliance as described in section [Adding IAM Roles](aws_iam_roles_add.md).

1. In the Encryption settings section, choose whether you want to encrypt the replicated snapshot with an AWS KMS key and specify the necessary KMS key.

For a KMS key to be displayed in the list of available encryption keys, it must be stored in the target AWS Region and the IAM role specified for the replication operation must have permissions to access the key. For more information on KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html).

1. At the Tags step of the wizard, choose whether you want to assign AWS tags to the created snapshot:

* To assign already existing AWS tags from the source DB instance and Aurora DB cluster, select the Copy tags from source RDS instance check box.

If you choose to copy tags from the source RDS resource, the backup appliance will first create a snapshot of the DB instance or Aurora DB cluster and assign to the created snapshot AWS tags with Veeam metadata. Then, the backup appliance will copy tags from the processed resource and assign the copied AWS tags to the snapshot.

* To assign your own custom AWS tags, click Add and specify the tags explicitly. To do that, in the Add Custom Tag window, specify a key and a value for the new AWS tag, and then click Apply. Note that you cannot add more than 5 custom AWS tags.

If you choose to add custom tags to the created snapshots, the backup appliance will assign the specified tags right after it creates a snapshot.

1. At the Summary step of the wizard, review configuration information, choose whether you want to proceed to the [Session Log page](aws_reporting.md#ui) to track the progress of snapshot creation, and click Finish.

[![Creating RDS Snapshot Manually](images/aws_rds_take_snapshot_tags.webp)](images/aws_rds_take_snapshot_tags.webp "Creating RDS Snapshot Manually")

Page updated 2026-05-21

