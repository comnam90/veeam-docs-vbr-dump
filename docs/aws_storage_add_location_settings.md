---
title: "Step 3. Configure Location Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_storage_add_location_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Configure Location Settings


At the Location step of the wizard, you can specify target locations where the backup appliance will keep restore points produced by all SLA-based backup policies that will have this storage template assigned.

|  |
| --- |
| Note |
| The Storage Template wizard does not allow you to configure location settings for cloud-native snapshots and snapshot replicas. By design, snapshots are stored in the same AWS Regions where the source EC2 instances reside, and you cannot change this behavior. However, you can use the Add SLA-Based Policy wizard to specify target locations for snapshot replicas — to do that, follow the instructions provided in section [Creating SLA-Based EC2 Backup Policies](aws_add_sla_policy_snapshot_settings.md). |

To configure location settings for image-level backups, specify a target location (a standard or an archive backup repository) where image-level backups will be stored. To do that, click the link in the Backups section or the Archives section. Then, select the necessary repository from the Default repository drop-down list in the Backup repository settings or the Archive repository settings window.

By default, the backup appliance will use the selected repository for all AWS Regions where the source EC2 instances reside. To instruct the backup appliance to use separate repositories for each region:

1. Set the Configure region-specific repositories toggle to On.
2. In the Region-specific backup repository settings or the Region-specific archive repository settings section, click Add Region.
3. In the Configure Region Settings window, choose a region and a repository that you want to use for this region.

For a repository to be displayed in the list of available repositories, it must be added to the backup appliance as described in section [Managing Backup Repositories](aws_repositories.md). If you have not added the repository to the backup appliance beforehand, you can do it without closing the Select Repository and Configure Region Settings windows. To do that, click Add and complete the Add Repository wizard.

|  |
| --- |
| Important |
| * To be able to choose a target location for archived backups, you must specify a target location for image-level backups first. * Consider that data encryption must be either enabled or disabled for backup and archive backup repositories. This means that you cannot select an encrypted standard backup repository and an unencrypted archive backup repository in one storage template. However, the selected repositories can have different encryption schemes (password and KMS encryption). |

[![Adding Storage Template](images/aws_storage_add_location_settings.webp)](images/aws_storage_add_location_settings.webp "Adding Storage Template")

Page updated 2026-06-01

