---
title: "Performing Veeam Threat Hunter Scan"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_session_veeam_threat_hunter_run.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Performing Veeam Threat Hunter Scan


To perform Veeam Threat Hunter scan during the restore session, do the following at the Secure Restore step of the restore wizard:

1. Enable the Scan restore points with Veeam Threat Hunter option.
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

1. If you want to continue Veeam Threat Hunter scan after the first malware is found, select the Continue scanning all remaining files after the first occurrence check box.


