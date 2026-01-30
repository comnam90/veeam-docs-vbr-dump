---
title: "Exporting Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/exporting_backups_hv.html"
last_updated: "12/12/2025"
product_version: "13.0.1.1071"
---

# Exporting Backups


Exporting backups allows you to synthesize a complete and independent full backup file out of selected restore points that are located in your backup repositories. You can transform any incremental or reverse-incremental backup chain (that is, all dependent .VBK, .VIB or .VRB files) into a full backup file and specify new retention policy settings for it. This option can be useful for legal hold and archiving purposes in case you want to prevent specific restore points from being deleted according to the retention policy of the primary backup job. It also allows you to provide a specific restore point on removable media.

|  |
| --- |
| Tip |
| Exporting backups allows you to export only a full backup file. If you want to export the whole backup chain, use the copy backup feature. For more information, see [Copying Backups](copy_backup_hv.md). |

Export applies to Full, Incremental and Reverse-incremental restore points located in:

* Backup repositories.
* Object storage repositories.
* Scale-out backup repositories.
* Backup repositories of cloud service providers and their tenants.

Consider the following:

* Once export is complete, exported backup files will be displayed under the Backups > Disk (Exported) node.
* [For scale-out backup repositories] If you export backups to another scale-out backup repository, Veeam Backup & Replication will synthesize these backups in the performance tier. If you export data to the same scale-out backup repositories, Veeam Backup & Replication will synthesize these backups in the same tier from which it was exported:

* If you export backups from the capacity tier, Veeam Backup & Replication synthesizes in the capacity tier. After a successful export, backups are displayed under the Backups > Capacity Tier (Exported) node.
* If you export from the archive tier, Veeam Backup & Replication retrieves them from the archive tier and then synthesizes in the archive tier. After a successful export, backups are displayed under the Backups > Archive Tier (Exported) node.

* [For scale-out backup repositories] The target location to which you export backup defines where Veeam Backup & Replication synthesizes the backups:

* If you export backups from the capacity tier to the same scale-out backup repositories, Veeam Backup & Replication synthesizes them in the capacity tier. After a successful export, backups are displayed under the Backups > Capacity Tier (Exported) node.
* If you export from the archive tier to the same scale-out backup repositories, Veeam Backup & Replication retrieves backups from the archive tier and then synthesizes them in the archive tier. After a successful export, backups are displayed under the Backups > Archive Tier (Exported) node.
* If you export backups to another scale-out backup repository, Veeam Backup & Replication will synthesize these backups in the performance tier.

|  |
| --- |
| Note |
| Note that the exported backup can be offloaded from the performance tier to the capacity or archive tier according to the settings of your scale-out backup repository. |

* If a restore point that is being exported resides on the tenant side, a new full backup file will also be exported to the same repository (on the tenant side) from which the source restore point is being taken.
* If a tenant initiates the export of a restore point that resides in the subtenant directory, a new full backup file will be exported to the tenant directory.
* If you select an encrypted backup job, the exported backup file will be encrypted with the same password that you set in the advanced job settings.
* If you export an immutable backup from a hardened repository to another hardened repository or to the same one, immutability is retained. If you export a backup from a hardened repository to a non-hardened repository, the immutability will be removed.

* You cannot export VBK files that were imported without their corresponding metadata file (VBM).

* If you select a backup job consisting of multiple virtual machines, Veeam will synthesize a separate full backup file per each machine.
* Export session results are saved to the configuration database and available for viewing, as described in section [Viewing Session Statistics](export_statistic_hv.md).

In This Section

* [Performing Export](performing_full_export_hv.md)
* [Viewing Session Statistics](export_statistic_hv.md)


