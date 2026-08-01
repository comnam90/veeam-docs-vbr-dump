---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_sla_based_policy_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you protect EC2 instances, consider the following prerequisites and requirements:

* If you plan to create image-level backups of EC2 instances, backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and configured properly. These include [backup repositories](aws_repositories_add_ui.md) and [worker instances](aws_workers.md).

* If you plan to create image-level backups of EC2 instances, backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and configured properly. These include [backup repositories](aws_repositories_add_ui.md) and [worker instances](aws_workers.md).

* If plan to create SLA-based backup policies, configure policy templates first. For more information, see [Managing SLA and Storage Templates](aws_sla_storage_manage.md).

* Veeam Plug-in for AWS prioritizes SLA-based backup policies over schedule-based backup policies. If an EC2 instance is included into both a schedule-based and an SLA-based backup policy, it will be processed by the SLA-based backup policy only.

* If you plan to create transactionally consistent backups of EC2 instances, check the requirements for application-aware processing and guest scripting. For more information, see sections [Creating Schedule-Based EC2 Backup Policies](aws_add_policy_guest_processing.md) and [Creating SLA-Based EC2 Backup Policies](aws_add_sla_policy_guest_processing.md).

* Veeam Plug-in for AWS protects only EC2 instances that run in VPCs. EC2-Classic instances are not supported. For more information, see [this Veeam KB article](https://www.veeam.com/kb3147).

When backup appliances back up EC2 instances with IPv6 addresses assigned, it does not save the addresses. That is why when you restore these instances, IP addresses are assigned according to the settings specified in AWS for the subnet to which the restored instances will be connected.

* Backup appliances may fail to create image-level backups of EC2 instances with [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes) if the AMIs that were used to deploy the instances do not support the type of worker instances deployed for the backup operation. To work around the issue, modify the worker profile to choose another instance type, as described in section [Managing Worker Profiles](aws_worker_profiles.md).

* [Applies only to image-level backups and file-level recovery from cloud-native snapshots] Veeam Plug-in for AWS does not support creating image-level backups and restoring EC2 instances with [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes) that have vendor restrictions preventing root EBS volumes from being attached to worker instances as secondary volumes. To learn how backup appliances perform EC2 backup, see [Protecting EC2 Instances](aws_backup_hiw_ec2.md).

* Veeam Plug-in for AWS does not support creating cloud-native snapshots and image-level backups for arm64-based EC2 instances if these instances were deployed from AMIs containing [product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes).

* Since Veeam Plug-in for AWS runs retention sessions for SLA-based backup policies as soon as it finalizes the data protection window in all protected regions, it is recommended that you estimate how long it may take for backup appliances to complete a retention session first, and then configure a backup window. Otherwise, Veeam Plug-in for AWS will not be able to run retention sessions, and obsolete data will not be removed from the appliance configuration database and backup repositories.

Page updated 2026-05-21

