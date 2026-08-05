---
title: "Step 8. Enable AWS Tags Assignment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_target_settings_rds_tags.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 8. Enable AWS Tags Assignment


At the
Tags
step of the wizard, you can choose whether you want to assign to cloud-native snapshots and snapshot replicas of the selected RDS resources already existing AWS tags and your own custom tags.

If you set the
Add custom tags to created snapshots
toggle to
On
, you must also specify the tags explicitly. To do that, use the
Key
and
Value
fields to specify a key and a value for the new custom AWS tag, and then click
Add
. Note that you cannot add more than 5 custom tags.

[![Creating RDS Backup Policy](images/aws_rds_backup_tags.webp)](images/aws_rds_backup_tags.webp "Creating RDS Backup Policy")

Page updated 2025-11-24

