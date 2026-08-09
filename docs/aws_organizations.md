---
title: "AWS Organizations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_organizations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# AWS Organizations


Veeam Plug-in for AWS allows you to protect AWS resources that belong to AWS accounts within AWS Organizations. To ensure flexibility in data protection, you can provide backup appliances full or limited access to account resources across organizational units.

How To Protect Resources Within AWS Organizations

To be able to perform data protection operations with AWS resources within an AWS Organization, perform the following steps:

1. [Check limitations and prerequisites](aws_limitations.md#organizations).
2. [Create at least 2 IAM role templates](aws_organization_template_add.md) that will help you configure IAM roles whose permissions will be used to perform the following actions:

* Organization rescan IAM role — permissions of this role will be used to collect information on the organization. Note that you will then have to create the role in the AWS account that is used to manage the organization (that is, the [management account](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#management-account) or a [delegated administrator account](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#delegated-admin)).
* Backup and restore IAM role — permissions of this role will be used to perform backup and restore operations with resources of the organization. Note that you will then have to create the role in each AWS account that contains resources you plan to protect within the organization.
* [Optional] Production worker IAM role — permissions of this role will be used to communicate with worker instances deployed in production accounts. The role will be attached to the worker instances to index EFS file systems, and to perform operations with EC2 and RDS resources within the AWS Organization. Note that you will then have to create the role in each AWS account that contains resources you plan to protect within the organization.

As soon as you create the templates, a backup appliance will export them to your workstation as .CFORM or .JSON files.

1. Create the necessary IAM roles in AWS:

* For templates in the CloudFormation format, upload the files to the AWS CloudFormation service and use these files to create the necessary IAM roles automatically, as described in [AWS Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html).
* For templates in the JSON format, use the files to create IAM policies in the IAM console and attach the policies to the necessary IAM roles manually, as described in [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md) and [Appendix B. Creating IAM Policies in AWS](aws_create_iam_policy.md).

1. [Add the Organization rescan IAM role to the backup appliance](aws_iam_roles_add.md).
2. [Add the AWS Organization to the backup appliance](aws_organizations_add.md). You will be able to choose whether you want to protect resources across the entire organization or across a limited scopes of organizational units.
3. [[Optional] Configure worker instance settings to deploy workers while indexing EFS file systems and processing EC2 and DB instance data](aws_workers.md).
4. [Create a backup policy and specify the AWS Organization as the data protection scope](aws_performing_backup_web_ui.md). You will be able to protect either the entire organization or a limited scope of organizational units.

|  |
| --- |
| Note |
| To learn how to perform disaster recovery operations with AWS resources within protected AWS Organizations, see [Performing Restore](aws_recovery.md). |

Page updated 2026-05-19

