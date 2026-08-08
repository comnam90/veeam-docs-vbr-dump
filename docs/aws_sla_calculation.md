---
title: "How Backup Appliances Estimate SLA Compliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_sla_calculation.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Backup Appliances Estimate SLA Compliance


To estimate SLA compliance for an SLA-based backup policy, the backup appliance performs the following steps:

1. Calculates the SLA compliance ratio individually for each EC2 instance added to the backup scope. The SLA compliance ratio equals a percentage of restore points successfully created for the instance out of the total number of restore points expected to be produced by the SLA-based backup policy for this instance.

When calculating the SLA compliance ratio for daily, weekly and monthly restore points, the backup appliance takes into account [snapshot and backup settings](aws_sla_add.md) configured while creating the SLA template that is assigned to the SLA-based backup policy.

1. Uses the ratios calculated at step 1 to determine the average SLA compliance ratio for the policy.
2. Compares the average SLA compliance ratio calculated at step 2 and the target SLA value configured for the policy. If the average SLA compliance ratio equals or is greater than the target SLA value, the backup appliance marks this policy as meeting SLA standards.

Impact of Backup Scope Changes on SLA Compliance Estimation

When calculating the SLA compliance ratio for each EC2 instance added to the backup scope of an SLA-based backup policy, the backup appliance estimates the total number of restore points expected to be produced for this instance based on the number of policy sessions remaining at the time when the instance was added to the backup scope. This means that when a [new EC2 instance is added](aws_add_sla_policy_source_settings.md#resources) to the backup scope (either manually or automatically) during the data protection window configured in the SLA template, the backup appliance considers all the preceding policy sessions as completed successfully for this instance.

|  |
| --- |
| Note |
| If an archive schedule and a monthly snapshot replica schedule are configured in the SLA template and a new EC2 instance is added to the backup scope after these monthly sessions have already run, the backup appliance will consider all preceding policy sessions as completed successfully for the new instance. The first actual archived and snapshot replica session for the instance will run in the next month according to the monthly schedule. |

Consider the following example. You configure an SLA-based backup policy to create daily backups every 1 hour between 10:00 AM and 6:00 PM, meaning that the total number of backups expected to be produced for all EC2 instances already included in the backup scope equals 8 per day. At 12:30 PM (after the 3rd backup session ends), you add a new instance to the backup scope, while the remaining number of backups expected to be produced equals 5. As soon as the backup appliance finalizes the backup window in all the protected AWS Regions, 3 backups that were to be produced during the first 3 backup sessions will be considered as created successfully — and the SLA compliance ratio for the newly added instance will be calculated depending on the results of the last 5 sessions:

* If the backup appliance successfully creates 5 backups (one per each of these 5 sessions), the SLA compliance ratio will equal (3 + 5) / 8 \* 100% = 100% for the instance.
* If the backup appliance successfully creates only 3 backups (meaning that 2 out of these 5 sessions fail to complete successfully), the SLA compliance ratio will equal (3 + 3) / 8 \* 100% = 75% for the instance.

Impact of SLA Template Changes on SLA Compliance Estimation

The backup appliance estimates SLA compliance for each SLA-based backup policy based on the schedule settings configured for the SLA template that is assigned to this policy. When you modify snapshot or backup settings for an SLA template or assign another template to an SLA-based backup policy, this affects the SLA compliance ratio retrospectively — meaning that the backup appliance recalculates the SLA compliance ratio for all entries on the SLA Compliance Overview chart.

For example, if an SLA-based backup policy configured to produce daily snapshots every 2 hours between 10:00 AM and 2:00 PM successfully creates 2 snapshots on time, this means that the SLA compliance ratio will be 100%. If you reconfigure the policy to produce daily snapshots every 1 hour between 10:00 AM and 2:00 PM, and if the policy successfully creates 4 snapshots on time, this means that the SLA compliance ratio will change to 50% on the SLA Compliance Overview chart.

To learn how to edit SLA template settings, see [Managing SLA Templates](aws_sla_edit.md).

Page updated 2026-05-21

