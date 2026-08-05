---
title: "Step 5. Finish Working with Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_organization_add_review.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Finish Working with Wizard


At the Summary step of the wizard, review configuration information and check whether the specified Organization rescan IAM role has all the required permissions, as well as whether the Backup and restore IAM role and Production worker IAM role exist in all AWS accounts within the organization — to do that, click Test Configuration. The backup appliance will display the Test organization configuration window where you can track the progress and view the results of the configuration check. If some permissions of the Organization rescan IAM role are missing, the check will complete with errors. You can grant the missing permissions to the IAM role using the AWS Management Console or [instruct the backup appliance to do it](aws_iam_roles_check.md). To learn how to grant permissions to IAM roles using the AWS Management Console, see [Appendix B. Creating IAM Policies in AWS](aws_create_iam_policy.md).

After the required permissions are granted, close the Test organization configuration window and review configuration information. Then, choose whether you want to proceed to the [Sessions page](aws_reporting.md#ui) to track the progress of adding the organization, and click Finish.

[![Adding AWS Organization](images/aws_organizations_add_summary.webp)](images/aws_organizations_add_summary.webp "Adding AWS Organization")

Page updated 2026-05-22

