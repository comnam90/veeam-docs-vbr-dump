---
title: "SLA Templates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_sla_template_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# SLA Templates


An SLA template is a collection of settings that allows you to protect your data according to a periodic backup schedule in a way the data protection complies with SLA standards in your company. These standards are defined by a specific target SLA value that indicates how much data you can afford to lose in case a disaster strikes, which allows you to troubleshoot backup issues and facilitate backup infrastructure audit.

The target SLA value is a percentage of successfully created restore points out of the total number of restore points expected to be produced by an SLA-based backup policy. Based on this percentage, backup appliances estimate the SLA compliance ratio for all SLA-based backup policies that have the related SLA template assigned. For more information, see [How Veeam Backup for AWS Estimates SLA Compliance](aws_sla_calculation.md).

One SLA template can be assigned to one or more SLA-based backup policies. When configuring an SLA template, you can create separate independent schedules for cloud-native snapshots, snapshot replicas, image-level backups and archived backups. For more information on how backup appliances build snapshot, snapshot replica, backup and archive backup chains, see sections [Snapshot Chain](aws_snapshot_chain.md), [Backup Chain](aws_backup_chain.md) and [Archive Backup Chain](aws_archive_chain.md).

|  |
| --- |
| Note |
| The way backup appliances produce image-level backups vary depending on the snapshot and backup settings configured for SLA templates. For more information, see [Reused and Temporary Snapshots](aws_temporary_restore_points.md). |

Related Topics

* [Data Protection Windows](aws_snapshot_backup_window.md)
* [Monitoring SLA-Based Policy Performance](aws_sla_monitoring.md)

Page updated 2026-05-19

