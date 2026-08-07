---
title: "Step 4. Specify IAM Role"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_s3_role.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify IAM Role


[This step applies only if you have added to the backup appliance multiple IAM roles belonging to the same AWS account]

At the
IAM Identity
step of the wizard, select an IAM role whose permissions will be used to create the repository and to access the target Amazon S3 bucket. For more information on the required permissions that must be assigned to the IAM role, see
[Restore IAM Permissions](aws_role_permissions_restore.md)
.

For an IAM role to be displayed in the
IAM role
drop-down list, it must be added to the backup appliance with the
Repository role
selected as described in section
[Adding IAM Roles](aws_iam_roles_specify_permissions.md)
, and must belong to the same AWS account to which the IAM user specified at
[step 3](aws_add_s3_account.md)
of the wizard belongs.

![Step 4. Specify IAM Role](images/aws_add_s3_role.webp "Add Amazon S3 repository - IAM role")

Page updated 2026-01-29

