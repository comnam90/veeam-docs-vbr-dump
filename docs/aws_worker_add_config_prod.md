---
title: "Adding Configurations for Production Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_worker_add_config_prod.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Configurations for Production Accounts


By design, the backup appliance deploys worker instances in production accounts to perform EFS indexing, RDS backup and RDS restore operations. You can [specify network settings](aws_worker_configurations_prod.md#region) that will be used to deploy these worker instances.

|  |
| --- |
| Note |
| If you want the backup appliance to deploy worker instances in production accounts to perform EC2 backup and restore operations as well (for example, to restore instances from cloud-native snapshots encrypted using default AWS managed keys), you must configure additional backup policy and restore settings. For more information, [Worker Deployment Options](aws_worker_options.md#production). |

To deploy worker instances in production accounts, the backup appliance employs the following IAM roles:

* An IAM role that is used to retrieve network settings of AWS Regions in a production account when adding new or editing existing working configurations. The role must be assigned permissions listed in section [Worker Configuration IAM Role Permissions](aws_role_permissions_service_prod_acc.md).

You must specify this IAM role either in the Add Organization wizard as described in [Adding AWS Organizations](aws_organization_add_settings.md), or in the Add Worker Configuration wizard as described in [Adding Worker Configurations](aws_worker_configuration_general_prod.md#IAMrole).

* An IAM role that is used to perform a backup or restore operation. The backup appliance also uses this role to deploy worker instances in a production account. That is why the role must be assigned additional permissions listed in section [EFS Backup IAM Role Permissions](aws_role_permissions_backup_efs.md#worker), [EC2 Backup IAM Role Permissions](aws_role_permissions_backup_ec2.md#worker), [EC2 Restore IAM Permissions](aws_role_permissions_restore_ec2.md#worker) or [RDS Backup IAM Role Permissions](aws_role_permissions_backup_rds.md#worker).

You must specify this IAM role either in the [organization settings](aws_organization_add_settings.md#backup_role) when adding an AWS Organization to the backup appliance, or in the backup policy or restore settings as described in section [Creating EFS Backup Policies](aws_add_policy_scope_efs.md#account), [Creating EC2 Backup Policies](aws_add_policy_scope.md), [Performing RDS Backup](aws_add_policy_scope_rds.md#account), [Performing Entire EC2 Instance Restore](aws_restore_entire_account.md#roles), [Performing Volume-Level Restore](aws_restore_volume_account.md#roles) or [Performing RDS Database Restore](aws_restore_rds_database_workers.md).

* An IAM role that is attached to the deployed worker instances and further used by the backup appliance to communicate with the instances. The role must be assigned permissions listed in section [Worker Deployment Role Permissions in Production Accounts](aws_role_permissions_prod_acc.md) or [FLR Worker IAM Role Permissions](aws_role_permissions_flr_prod.md).

You must specify this IAM role either in the [organization settings](aws_organization_add_settings.md#backup_role) when adding an AWS Organization to the backup appliance, or when enabling worker deployment in production accounts in the backup policy or restore settings, as described in section [Creating EFS Backup Policies](aws_add_policy_indexing_efs.md#enable_efs_indexing), [Creating EC2 Backup Policies](aws_add_policy_target_settings_backups.md#workers), [Creating RDS Backup Policies](aws_add_policy_target_settings_backups_rds.md), [Performing Entire EC2 Instance Restore](aws_restore_entire_account.md#workers), [Performing Volume-Level Restore](aws_restore_volume_account.md#workers), [Performing File-Level Recovery](aws_restore_item_mode.md#workers) or [Performing RDS Database Restore](aws_restore_rds_database_workers.md).

|  |
| --- |
| Note |
| Since you do not specify an IAM role for file-level recovery operations, the role that you specify when enabling worker deployment in production accounts in the restore settings is also used by the backup appliance to deploy worker instances. |

Related Topics

* [Editing Configurations](aws_worker_settings_edit.md)
* [Removing Configurations](aws_worker_remove_config.md)

Page updated 2026-05-20

