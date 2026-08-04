---
title: "Step 6. Configure RDS Resource Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Configure RDS Resource Settings


[This step applies only if you have selected the
Restore to new location, or with different settings
option at the
Restore Mode
step of the wizard]

At the
Settings
step of the wizard, specify settings for the restored RDS resources. To do that, follow the instructions provided in sections
[Configuring Settings for DB Instances](aws_restore_rds_instance_settings.md)
and
[Configuring Settings for Aurora DB Clusters](aws_restore_rds_cluster_settings.md)
.

|  |
| --- |
| Tip |
| The  Settings  step also contains some preconfigured settings retrieved from the source RDS resources. If you want to specify advanced configuration settings for a restored DB instance or Aurora DB cluster, select the necessary resource and click  Advanced Options . For more information on all available settings that can be specified for RDS resources, see the  [Amazon RDS User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html#USER_CreateDBInstance.Settings)  and  [Amazon Aurora User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.CreateInstance.html#Aurora.CreateInstance.Settings) . |

Page updated 2026-01-30

