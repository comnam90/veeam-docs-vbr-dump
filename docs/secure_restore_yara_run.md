---
title: "Performing YARA Scan"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/secure_restore_yara_run.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Performing YARA Scan

In this article

To perform the YARA scan during the restore session, do the following at the Secure Restore step of the restore wizard:

1. Enable the Scan the restore point with the following YARA rule option.
2. Place the YARA file with the .yara or .yar extension in the C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules folder (for Veeam Backup & Replication on Microsoft Windows) or in the /var/lib/veeam/yara\_rules/ directory (for Veeam Backup & Replication on Linux). You can add the file through the File view in the Veeam Backup & Replication console. For more information, see [Copying Files and Folders Manually](copying_files_and_folders.md).

For more information on how to create a YARA rule, see [YARA documentation](https://yara.readthedocs.io/en/stable/writingrules.html).

1. Specify the behavior scenario if malware activity is found. For more information about available options, see the following sections:

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

1. If you want to continue the YARA scan after the first malware is found, select the Continue scanning all remaining files after the first occurrence check box.

Note that if the YARA rule is not found, Veeam Backup & Replication will display a warning. In that case, to pass the step with secure restore settings, you can do one of the following:

* Make sure that the YARA file is located in the required directory, has the proper syntax and the .yara or .yar extension.
* Clear the Scan the restore point with the following YARA rule option.
* Use Veeam Threat Hunter or third-party antivirus sofware. For more information, see [Veeam Threat Hunter for Secure Restore](secure_restore_veeam_threat_hunter.md) and [Antivirus Scan for Secure Restore](secure_restore_antivirus.md).

Page updated 11/26/2025

Page content applies to build 13.0.1.1071
