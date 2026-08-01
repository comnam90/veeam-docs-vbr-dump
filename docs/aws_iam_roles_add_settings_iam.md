---
title: "Specifying Settings for IAM Role from Initial Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_iam_roles_add_settings_iam.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Settings for IAM Role from Initial Account


[This step applies only if you have selected the IAM role from current account option]

At the Type step of the wizard, use the IAM role name field to enter the IAM role name as specified in AWS. If the IAM role was created with a path, you must specify the full path and the name of the IAM role. For example, /dept\_1/backup\_role.

|  |
| --- |
| Important |
| To allow the backup appliance to assume the IAM role, you must configure trust relationships for the role as described in section [Before You Begin](aws_byb_roles.md). |

[![IAM Role Current Account](images/aws_iam_roles_add_role.webp)](images/aws_iam_roles_add_role.webp "IAM Role Current Account")

Page updated 2026-05-20

