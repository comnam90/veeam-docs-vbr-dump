---
title: "Reused and Temporary Snapshots"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_temporary_restore_points.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Reused and Temporary Snapshots


When running an SLA-based backup policy, a backup appliance produces image-level backups differently, depending on the [snapshot and backup settings](aws_sla_add.md) configured for the SLA template that is assigned to this policy.

Reused Snapshots

If the snapshot and backup settings are configured in a way that snapshot sessions and backup sessions start at the same time, the backup appliance re-uses the cloud-native snapshots created by the snapshot sessions instead of taking new cloud-native snapshots during every backup session. The retention of these snapshots depends on whether you enable the changed block tracking (CBT) mechanism for the SLA template:

* If CBT is enabled, the backup appliance keeps each of the re-used cloud-native snapshots in the snapshot chain until the next image-level backup session completes. In this case, the appliance processes only those data blocks that have changed since the previous snapshot was created. This allows you to increase the speed and efficiency of incremental backups but can incur additional costs of storing snapshots in AWS.
* If CBT is disabled, the backup appliance keeps each of the re-used cloud-native snapshots in the snapshot chain according to the retention settings specified while creating the SLA template.

If the retention period ends before the next backup session starts, the backup appliance processes not only those data blocks that have changed since the previous snapshot was created, but also all other data blocks of the snapshot. This allows you to reduce the cost of storing snapshots in AWS but decreases the speed and efficiency of incremental backups.

If the retention period ends after the next backup session starts, the backup appliance processes only those data blocks that have changed since the previous snapshot was created. This allows you to increase the speed and efficiency of incremental backups but can incur additional costs of storing snapshots in AWS.

Temporary Snapshots

If the snapshot and backup settings are configured in a way that snapshot sessions and backup sessions start at a different time, the backup appliance takes temporary snapshots that will be used to create image-level backups and will be then removed automatically. The retention of these snapshots depends on whether you enable the changed block tracking (CBT) mechanism for the SLA template:

* If CBT is enabled, the backup appliance keeps each of the temporary snapshots in the snapshot chain until the next image-level backup session starts. In this case, the backup appliance processes only those data blocks that have changed since the previous snapshot was created. This allows you to increase the speed and efficiency of incremental backups but can incur additional costs of storing snapshots in AWS.
* If CBT is disabled, the backup appliance removes each of the temporary snapshots after the image-level backup session completes. In this case, the backup appliance processes not only those data blocks that have changed since the previous snapshot was created, but also all other data blocks of the snapshot. This allows you to reduce the cost of storing snapshots in AWS but decreases the speed and efficiency of incremental backups.

|  |
| --- |
| Important |
| * It is recommended that you do not remove temporary snapshots from AWS manually. * It is recommended that you take into account both backup schedules and your cost management strategy when choosing whether to enable CBT for SLA templates. |

Related Topics

* [Changed Block Tracking](aws_cbt.md)
* [CBT Impact on Snapshot Retention](aws_cbt_retention.md)

Page updated 2026-05-19

