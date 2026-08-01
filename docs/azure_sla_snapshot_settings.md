---
title: "Step 3. Configure Snapshot Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sla_snapshot_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Configure Snapshot Settings


At the Snapshots step of the wizard, you can configure the following snapshot settings:

1. In the Snapshots section, you can instruct the backup appliance to create cloud-native snapshots on a daily, weekly and monthly basis, and to keep the created snapshots in a snapshot chain for a specific number of days, months or years. If a snapshot is older than the specified time limit, the backup appliance removes the snapshot from the chain.

Note that if you configure a schedule but do not select the corresponding check box, Veeam Backup for Microsoft Azure will ignore the specified settings and will not create snapshots according to this schedule.

1. In the Snapshot window section, you can instruct the backup appliance to create daily snapshots within a specific time interval if you do not want backup operations to overlap production hours.

The backup appliance automatically adjusts the specified snapshot window to the time zone of each region added to all SLA-based backup policies that have this SLA template assigned. For more information, see [Data Protection Windows](azure_snapshot_backup_window.md).

When you combine multiple types of snapshot schedules, the backup appliance re-uses snapshots created according to a more-frequent schedule (daily or weekly) to achieve the desired SLA compliance for less-frequent schedules (weekly and monthly). For example, if you configure a daily and a monthly schedule, the first snapshot successfully created according to the daily schedule will be marked as both a daily and a monthly snapshot.

[![Adding SLA Policy](images/azure_sla_snapshot_settings.webp)](images/azure_sla_snapshot_settings.webp "Adding SLA Policy")

Page updated 2026-07-01

