---
title: "Step 6. Configure File System Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_type_efs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Configure File System Settings


[This step applies only if you have selected the
Restore to new location, or with different settings
option at the
Restore Mode
step of the wizard]

At the
Settings
step of the wizard, you can specify new names and configuration settings for the restored file system.

To specify a new name, select the file system and click
Rename
. In the
File system name
window, specify the name and click
Apply
.

To specify configuration settings, do the following:

1. Select the file system and click
   Edit
   .
2. In the
   General Settings
    window, do the following:

1. From the
   Storage class availability
    drop-down list, select one of the following options:

* Regional
   — if you want to redundantly store data of the restored file system across all Availability Zones within the selected AWS Region.

* One Zone
   — if you want to redundantly store data of the restored file system within a single Availability Zone.

1. [Applies only if you have selected the
   Regional
    option] From the
    Performance mode
    drop-down list, select a performance mode for the restored file system. For more information on performance modes, see
   [AWS Documentation](https://docs.aws.amazon.com/efs/latest/ug/performance.html#performancemodes)
   .
2. [Applies only if you have selected the
   One Zone
    option] From the
   Availability zone
    drop-down list, select an Availability Zone where the restored file system will be located.

1. To save changes made to the file system settings, click
   Apply
   .

[![Restoring EFS File Systems](images/aws_restore_entire_general_settings_efs.webp)](images/aws_restore_entire_general_settings_efs.webp "Restoring EFS File Systems")

Page updated 2026-01-30

