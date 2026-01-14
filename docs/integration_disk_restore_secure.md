---
title: "Step 6. Specify Secure Restore Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_disk_restore_secure.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Step 6. Specify Secure Restore Settings

In this article

At the Secure Restore step of the wizard, you can instruct Veeam Backup & Replication to perform secure restore — scan restored disk data with antivirus software before restoring the disk. To learn more about secure restore, see [Secure Restore](av_scan_about.md).

To specify secure restore settings:

1. In the Content scan section, specify the following:

1. If you want to scan the restored volume with a scan engine or antivirus software, select the method you want to use for data scan:

* Select the Scan restore points with Veeam Threat Hunter option to use Veeam Threat Hunter.

This option is available if you configured Veeam Threat Hunter as the detection engine in the malware detection settings. To learn more, [Signature Detection](malware_detection_signature_detection.md).

* Select the Scan restore points with your existing antivirus software option to use third-party antivirus software.

This option is available if you configured a third-party antivirus as the detection engine in the malware detection settings. To learn more, [Signature Detection](malware_detection_signature_detection.md).

|  |
| --- |
| Tip |
| Click Change to open the Malware Detection Settings window where you can change the detection engine to Veeam Threat Hunter. |

1. To use a YARA rule as a scan engine, select the Scan the restore point with the following YARA rule check box and choose a YARA rule from the drop-down list. By default, the paths to the YARA rules are as follows:

* /var/lib/veeam/yara\_rules directory — if you use Veeam Backup & Replication on Linux.
* C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules — if you use Veeam Backup & Replication on Microsoft Windows.

1. Instruct Veeam Backup & Replication what to do in case malware is found:

* Select Proceed with recovery if you want to continue the recover process, despite the found malware threat.
* Select Abort disk recovery if you want to stop the recovery process after the first malware threat is found.

1. In the Scan options section, select the Continue scanning all remaining files after the first occurrence check box if you want the antivirus software to continue volume scan after the first malware threat is found. For information on how to view results of the antivirus scan, see [Viewing Malware Scan Results](av_scan_log.md).

![Step 6. Specify Secure Restore Settings](images/agent_restore_disks_secure.webp "Specify Secure Restore Settings")

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
