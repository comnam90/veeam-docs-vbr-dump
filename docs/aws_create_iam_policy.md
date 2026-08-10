---
title: "Appendix B. Creating IAM Policies in AWS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_iam_policy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix B. Creating IAM Policies in AWS


|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see AWS Documentation. |

When you [create an IAM role](aws_create_iam_policy_role.md), you must define permissions that the role will have in AWS. To define the role permissions, you must create an IAM policy and attach it to the IAM role. For more information on managing IAM identity permissions, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html#add-policies-console).

To create an IAM policy using the AWS Management Console, do the following:

1. Log in to the AWS Management Consoleusing credentials of an AWS account in which you want to create the IAM policy.
2. Navigate to All Services > Security, Identity, & Compliance and click IAM.
3. In the Amazon IAM console, navigate to Access Management > Policies and click Create policy.
4. Complete the Create policy wizard:

1. At the Editor step of the wizard, switch to the JSON tab.
2. Type or paste a JSON policy document.

The JSON policy document must include permissions required for an IAM role to which you want to attach the policy. For more information on required permissions, see [IAM Permissions](aws_system_requirements_permissions.md). To learn how to write JSON policy documents, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html).

|  |
| --- |
| Important |
| Consider the following AWS limitations on IAM policy sizing:   * The size of a managed IAM policy cannot exceed 6.144 characters. For more information on managed IAM policies, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#customer-managed-policies). * The total size of all inline IAM policies added to an IAM role cannot exceed 10.240 characters. For more information on inline IAM policies, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#inline-policies).   For more information on IAM character limits, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html#reference_access-analyzer-quotas). |

1. At the Tags step of the wizard, specify AWS tags that will be assigned to the IAM policy.
2. At the Review step of the wizard, specify a name and description for the IAM policy. Review the configured settings and click Create policy.

After you create a policy, you can attach it to IAM roles as described in section [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).

Page updated 2026-05-20

