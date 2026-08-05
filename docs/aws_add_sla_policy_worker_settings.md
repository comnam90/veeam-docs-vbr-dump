---
title: "Step 8. Configure Worker Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_sla_policy_worker_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 8. Configure Worker Settings


By default, the backup appliance deploys worker instances used to perform backup operations in the [backup account](aws_worker_options.md). However, you can instruct the backup appliance to deploy worker instances in a production account — that is, the same AWS account to which the processed resources belong. To do that, set the Deploy workers in production account toggle to On.

Depending on the option selected at [step 3](aws_add_sla_policy_scope.md) of the wizard, the following will happen:

* If you have selected the Account option, you will be able to choose an IAM role that will be attached to the worker instances and used by the backup appliance to communicate with these instances. The role you choose must belong to the same account to which the IAM role specified for the backup operation belongs, and must be assigned the permissions listed in section [Worker Deployment Role Permissions in Production Accounts](aws_role_permissions_prod_acc.md#worker_reqs).

For an IAM role to be displayed in the list of available roles, it must be added to the backup appliance with the Production worker role selected as described in section [Adding IAM Roles](https://helpcenter.veeam.com/docs/vbaws/guide/iam_roles_add.html). If you have not added the necessary IAM role to the backup appliance beforehand, you can do it without closing the Add Policy wizard. To do that, click Add and complete the Add IAM Role wizard.

* If you have selected the Organization option, the backup appliance will automatically choose an IAM role that will be attached to the worker instances and used by the backup appliance to communicate with these instances. It will be one of the roles specified in the settings of the selected organization identity — either the IAM role whose permissions will be used to perform the backup operation (that is, the Backup and restore IAM role), or the IAM role that will be attached to the worker instances and used by the backup appliance to communicate with these instances (that is, the Production worker IAM role).

For the backup appliance to be able to choose an IAM role automatically, it must be created in all AWS accounts belonging to the selected organization identity, and specified in the organization settings as described in section [Adding AWS Organizations](aws_organization_add_settings.md#backup_role) (step 3).

|  |
| --- |
| Important |
| * If you instruct the backup appliance to deploy worker instances in production accounts, you must assign additional permissions to the IAM role used to perform the backup operation. For more information on the required permissions, see [EC2 Backup IAM Role Permissions](aws_role_permissions_backup_ec2.md).  * [Applies only if you have chosen the Account option at the Source step of the wizard] It is recommended that you check whether both the IAM role specified at [step 3](aws_add_sla_policy_scope.md#account) of the wizard and the IAM role specified in the Backups section have the required permissions — if some of the permissions are missing, the backup policy may fail to complete successfully. To run the IAM role permission check, click Check Permissions and follow the instructions provided in section [Checking IAM Role Permissions](aws_iam_roles_check.md#wizard).  * The backup appliance may fail to create image-level backups of EC2 instances with [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes) if the AMIs that were used to launch the instances do not support the type of worker instances deployed for the backup operation. To work around the issue, modify the worker profile to choose another instance type, as described in section [Managing Worker Profiles](aws_worker_profiles.md).  * The backup appliance does not support backup of EC2 instances with [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html) that have vendor restrictions preventing root EBS volumes from being attached to worker instances as secondary volumes. To learn how backup appliances perform EC2 backup, see [Protecting EC2 Instances](aws_backup_hiw_ec2.md). |

[![Creating SLA-Based EC2 Policy](images/aws_add_sla_policy_worker_settings.webp)](images/aws_add_sla_policy_worker_settings.webp "Creating SLA-Based EC2 Policy")

Page updated 2026-05-22

