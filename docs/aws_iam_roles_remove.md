---
title: "Removing IAM Roles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_iam_roles_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing IAM Roles


The backup appliance allows you to permanently remove an IAM role from the appliance configuration database if it is no longer used to perform data protection and disaster recovery operations:

1. Switch to the Configuration page.

1. Navigate to Infrastructure > IAM Roles.

1. Select the IAM role and click Remove.

1. In the Remove IAM Role window, click Yes to acknowledge the operation.

|  |
| --- |
| Important |
| You cannot remove an IAM role that is used to access backup repositories or is specified in the settings of any configured backup policy. |

[![Removing IAM Roles](images/aws_iam_roles_remove.webp)](images/aws_iam_roles_remove.webp "Removing IAM Roles")

Page updated 2026-05-21

