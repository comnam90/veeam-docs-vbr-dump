---
title: "Comparing VPC Configuration Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backups_compare_vpc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Comparing VPC Configuration Backups


You can compare the attributes of the current Amazon VPC configuration to the attributes of a backed-up Amazon VPC configuration. To do that:

1. Navigate to Protected Data > VPC.
2. Select the necessary configuration record.
3. Click Compare.

By default, the backup appliance uses the most recent valid restore point. However, you can compare the VPC configuration data to an earlier state. To do that, click the Restore point link in the Compare Attributes window.

|  |
| --- |
| Tip |
| You can use the selected restore point to restore or export the VPC configuration. To do that, click either Restore or Export, and follow the instructions provided in section [Performing Entire Configuration Restore](aws_vpc_entire_restore.md) or [Performing Entire Configuration Export](aws_vpc_entire_export.md). |

[![Comparing VPC Configuration Backups](images/aws_vpc_backup_compare.webp)](images/aws_vpc_backup_compare.webp "Comparing VPC Configuration Backups")

Page updated 2026-05-21

