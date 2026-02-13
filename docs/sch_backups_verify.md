---
title: "Verifying Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backups_verify.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Verifying Backups


To perform an integrity check of VM backups, Veeam Backup & Replication offers the SureBackup technology that allows you to ensure that the created restore points are not corrupted. For backups of Windows VMs, you can also scan the restore points with antivirus software installed on the backup server, and run YARA rules to detect malware and sensitive data.

To create a SureBackup job, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs > Backup and click SureBackup Job on the ribbon.
3. At the Name step of the New SureBackup Job wizard, select the Backup verification and content scan only verification mode, and then complete the wizard as described in section [Creating SureBackup Jobs](create_surebackup_job.md).

If any of the verification checks fail for a restore point, Veeam Backup & Replication will mark both this restore point and all subsequent points in the backup chain as Infected. To learn how to manage infected restore points, see section [Managing Malware Status](malware_detection_managing_status.md).

|  |
| --- |
| Tip |
| You can scan backups of Windows VMs manually on demand, without creating a SureBackup job. To learn how to do that, see section [Scan Backup](malware_detection_scan_backup.md). |

[![Verifying Backups](images/sch_backups_verify.webp)](images/sch_backups_verify.webp "Verifying Backups")


