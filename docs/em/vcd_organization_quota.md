---
title: "About Organization Quota"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_organization_quota.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# About Organization Quota


When setting up an organization configuration, you specify a repository storage quota for the organization. This quota defines the amount of data that the organization's backup jobs can send to the dedicated backup repository or scale-out backup repository.

When calculating used quota, Veeam Backup Enterprise Manager takes into account the data compression and deduplication performed by Veeam Backup & Replication. However, all 3rd party compression and deduplication performed after the data is transferred to the repository (for example, by ReFS and XFS file systems or by cloud services) does not have effect on the used quota calculation.

The used quota is recalculated every time any of the organization jobs runs. If you manually remove backup files from a backup repository, the used quota will be recalculated after a job of this organization completes.

|  |
| --- |
| Note |
| * Replication jobs and CDP policies do not consume storage quota of backup repositories because replicas are stored on the target VMware Cloud Director VDC. If you want to set a quota for replicas, configure storage policies of the target VDC. * Quota calculation is not currently supported for capacity and archive tiers of scale-out backup repositories. |

Managing Backups and Used Quota

If you want to protect backups created by organizations, you can create backup copy jobs on your backup server. The size of backup files copied by backup copy jobs is not included in the used quota calculation. For more information about backup copy jobs, see the [Backup Copy](https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy.html?ver=13) section of the Veeam Backup & Replication User Guide.

You can also manually copy or move an organization backup from one backup repository to another. You may need to move some backups to another repository, for example, if the quota limit of one of the organization repositories is reaching. When you copy or move a backup to another repository, the used quota will be recalculated. For more information on copying and moving backups, see the [Copying Backups](https://helpcenter.veeam.com/docs/vbr/userguide/copy_backup.html?ver=13) and [Moving Backups](https://helpcenter.veeam.com/docs/vbr/userguide/move_backup.html?ver=13) sections of the Veeam Backup & Replication User Guide. Before you copy or move an organization backup, make sure that the organization has access to the target repository. To provide the access, add a new organization configuration for this repository. For details, see [Adding Organization Configuration](em_configure_vcd_org.md).


