---
title: "Verifying Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_verify_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Verifying Backups


To perform an integrity check of backups, Veeam Backup & Replication offers the SureBackup technology that allows you to ensure that the created restore points are not corrupted. You can also scan the restore points with antivirus software installed on the backup server, and run YARA rules to detect malware and sensitive data.

To create a SureBackup job, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Jobs and click SureBackup Job on the ribbon.
3. At the Name step of the New SureBackup Job wizard, select the Backup verification and content scan only verification mode, and then complete the wizard as described in the Veeam Backup & Replication, section [Creating SureBackup Jobs](surebackup_job_name_vm.md).

If any of the verification checks fail for a restore point, Veeam Backup & Replication will mark both this restore point and all subsequent points in the backup chain as Infected. To learn how to manage infected restore points, see [Managing Malware Status](malware_detection_managing_status.md).

|  |
| --- |
| Tip |
| You can scan backups of VMs manually on demand, without creating a SureBackup job. To learn how to do that, see [Scan Backup](https://helpcenter.veeam.com/docs/backup/vsphere/malware_detection_scan_backup.html?ver=120). |

[![Verifying Backups](images/aws_verifying_backups.webp)](images/aws_verifying_backups.webp "Verifying Backups")

Page updated 2026-05-22

