---
title: "Starting and Stopping Schedule-Based Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup_policy_start_stop.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Starting and Stopping Schedule-Based Backup Policies


You can start a schedule-based backup policy manually, for example, if you want to create an additional restore point in the snapshot or backup chain and do not want to modify the configured policy schedule. You can also stop a schedule-based backup policy if processing of an Azure resource is about to take too long, and you do not want the policy to have an impact on the production environment during business hours.

|  |
| --- |
| Important |
| In Veeam Backup for Microsoft Azure version 13, you cannot start or stop SLA-based backup policies manually — as a workaround, you can [enable or disable the policy](azure_backup_policy_enable_disable.md). |

To start or stop a schedule-based backup policy, do the following:

1. Navigate to Policies.
2. Switch to the necessary tab and select the backup policy.
3. Click Start or Stop.

[![Starting Backup Policy](images/azure_policy_start.webp)](images/azure_policy_start.webp "Starting Backup Policy")

Page updated 2026-07-28

