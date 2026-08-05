---
title: "Worker IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_service.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Worker IAM Permissions


Depending on whether you plan to deploy worker instances in the backup account or in production accounts, IAM roles used for worker instance deployment and communication with the instances must have a specific set of permissions:

* [IAM role permissions required in the backup account](aws_role_permissions_backup_acc.md).
* [IAM role permissions required in production accounts](aws_role_permissions_prod_acc.md).

For more information on AWS accounts in which backup appliances deploy worker instances, see [Worker Deployment Options](aws_worker_options.md).

Page updated 2026-05-19

