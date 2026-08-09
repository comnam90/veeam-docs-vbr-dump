---
title: "Starting and Stopping Schedule-Based Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_policies_start_stop.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Starting and Stopping Schedule-Based Policies


You can start a schedule-based backup policy manually, for example, if you want to create an additional restore point in the snapshot or backup chain and do not want to modify the configured backup policy schedule. You can also stop a backup policy if processing of an instance is about to take too long, and you do not want the policy to have an impact on the production environment during business hours.

To start or stop a schedule-based backup policy, do the following:

1. Navigate to Policies.
2. Switch to the necessary tab and select the backup policy.

1. Click Start or Stop.

|  |
| --- |
| Notes |
| * The created restore points will be retained for the time period specified in the most frequent backup policy schedule.  * [Applies only to EC2 backup policies] If the backup policy stores backups in a backup repository with immutability settings enabled, the created restore points will be immutable for the time period determined based on the retention settings specified in the most frequent backup policy schedule. For more information, see [Immutability](aws_immutability.md). |

[![Starting and Stopping Schedule-Based Policies](images/aws_policies_start_stop.webp)](images/aws_policies_start_stop.webp "Starting and Stopping Schedule-Based Policies")

Page updated 2026-05-21

