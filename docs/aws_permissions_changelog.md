---
title: "IAM Permissions Changelog"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_permissions_changelog.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# IAM Permissions Changelog


This section describes the latest changes in IAM permissions required for Veeam Plug-in for AWS to perform operations.

When you update a backup appliance version 10 to version 11, consider that additional permissions must be granted to the following IAM roles:

* For the backup appliance to be able to back up EC2 instances, the IAM roles specified in the [organization settings](aws_organization_add_settings.md) or in the [EC2 backup policy settings](aws_add_policy_scope.md) must be granted the following additional permissions:

|  |
| --- |
| "ebs:GetSnapshotBlock",  "kms:Decrypt" |

* For the backup appliance to be able to estimate the cost of creating cloud-native snapshots, snapshot replicas and image-level backups of EC2 instances, IAM roles that will be attached to the worker instances and used by the backup appliance to communicate with these instances must be granted the following additional permission:

|  |
| --- |
| "pricing:GetProducts" |

Page updated 2026-07-21

