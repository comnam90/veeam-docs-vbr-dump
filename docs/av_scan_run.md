---
title: "Performing Antivirus Scan"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/av_scan_run.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Performing Antivirus Scan

In this article

To perform the antivirus scan during the restore session, do the following at the Secure Restore step of the restore wizard:

1. Enable the Scan restore points with the existing antivirus software option.
2. Specify the behavior scenario if malware activity is found. For more information about available options, see the following sections:

* VMware vSphere:

* [Secure Restore settings for Instant Recovery to VMware vSphere](instant_recovery_av_vm.md)
* [Secure Restore settings for Instant Disk Recovery](instant_disk_recovery_secure_restore.md)
* [Secure Restore settings for Entire VM Restore](full_restore_av_vm.md)
* [Secure Restore settings for Virtual Disk Restore](disk_restore_av_vm.md)

* Microsoft Hyper-V:

* [Secure Restore settings for Instant Recovery to Microsoft Hyper-V](ir_secure_restore_hv.md)
* [Secure Restore settings for Entire VM Restore](full_restore_av_hv.md)

* [Secure Restore settings for Disk Export](disk_export_av.md)
* [Secure Restore settings for Restore to Microsoft Azure](restore_azure_av.md)
* [Secure Restore settings for Restore to Amazon EC2](restore_amazon_av.md)
* [Secure Restore settings for Restore to Google Compute Engine](restore_google_secure_restore.md)

1. If you want to continue the antivirus scan after the first malware is found, select the Continue scanning all remaining files after the first occurrence check box.

|  |
| --- |
| Note |
| For ESET NOD32 Antivirus version 9 and earlier, the Continue scanning all remaining files after the first occurrence option is supported with limitations. If the option is not selected, the antivirus scan will continue for the volume where malware activity was detected. Other volumes will not be scanned. |

If the antivirus is not installed or the configuration file has syntax errors, Veeam Backup & Replication will display a warning. In that case, to pass the step with secure restore settings, you can do one of the following:

* Set up the antivirus software properly.
* Clear the Scan restore points with the existing antivirus software option.
* Use Veeam Threat Hunter. For more information, see [Veeam Threat Hunter for Secure Restore](secure_restore_veeam_threat_hunter.md).
* Use YARA scan. For more information, see [YARA Scan for Secure Restore](secure_restore_yara.md).

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
