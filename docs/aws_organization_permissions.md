---
title: "Organization Rescan IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_organization_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Organization Rescan IAM Permissions


To allow a backup appliance to collect information on AWS Organizations, the Organization rescan IAM role specified in the [organization settings](aws_organization_add_settings.md) must meet the following requirements:

1. The backup appliance must be granted permissions to assume the IAM role. For more information on the requirements for adding IAM roles, see [Before You Begin](aws_byb_roles.md).

1. The IAM role must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Effect": "Allow",             "Action": [                 "iam:GetContextKeysForPrincipalPolicy",                 "iam:ListAccountAliases",                 "iam:SimulatePrincipalPolicy",                 "organizations:DescribeAccount",                 "organizations:DescribeOrganizationalUnit",                 "organizations:DescribeOrganization",                 "organizations:ListChildren",                 "organizations:ListRoots"             ],             "Resource": "\*"         }     ]  } |

To learn how to create IAM roles and assign them the required permissions, see [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-19

