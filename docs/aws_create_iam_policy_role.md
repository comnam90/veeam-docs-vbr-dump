---
title: "Appendix A. Creating IAM Roles in AWS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_iam_policy_role.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix A. Creating IAM Roles in AWS


|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see AWS Documentation. |

You must specify an IAM role for each data protection and disaster recovery operation performed by a backup appliance — the solution uses permissions of the specified IAM roles to access AWS services and resources. You can either [create an IAM role using the backup appliance](aws_iam_roles_add_settings_iam_new.md), or, first create the role in AWS using the AWS Management Console, [AWS CLI](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html#roles-creatingrole-service-cli) or [AWS API](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html#roles-creatingrole-service-api), and then [add this role to the backup appliance](aws_iam_roles_add_settings.md)

This section describes how to create an IAM role for the backup appliance using the AWS Management Console. To do that:

1. Log in to the AWS Management Consoleusing credentials of an AWS account in which you want to create the IAM role.
2. Navigate to All Services > Security, Identity, & Compliance and click IAM.
3. In the Amazon IAM console, navigate to Access Management > Roles and click Create role.
4. Complete the Create role wizard:

1. At the Select trusted entity step of the wizard, do either of the following:

* If you want to create the IAM role in the initial AWS account to which the backup appliance belongs, select the Custom trust policy option. Then, in the Custom trust policy section, add the following statement to allow the [Impersonal IAM role](aws_byb_roles.md) to assume the role you want to create:

|  |
| --- |
| {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": "sts:AssumeRole",       "Principal": {         "AWS": "<Role ARN>"       }     }   ]  } |

Where <Role ARN> is the ARN of the Impersonation IAM role. To obtain the ARN of the Impersonation IAM role, you can look it up on the Roles page in the AWS Management Console.

* If you want to create the IAM role in another AWS account, select the AWS account option. Then, in the An AWS account section, select the Another AWS account option and enter the ID of the trusted account — the AWS account to which the backup appliance belongs.

If you want to increase the security of the role, select the Require external ID check box and enter a password. To learn how to use an external ID to increase security of an IAM role, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html).

1. At the Add permissions step of the wizard, select an IAM policy that must be attached to the IAM role.

For an IAM policy to be displayed in the list, it must be created beforehand as described in section [Appendix B. Creating IAM Policies in AWS](aws_create_iam_policy.md).

1. At the Role details step of the wizard, specify a name and description for the IAM role.
2. At the Tags step of the wizard, specify AWS tags that will be assigned to the IAM role.
3. Click Create role.

1. Add the created IAM role to the configuration database of the backup appliance as described in section [Adding IAM Roles](aws_iam_roles_add.md).

Page updated 2026-06-23

