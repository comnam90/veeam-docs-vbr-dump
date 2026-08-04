---
title: "Secure Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/av_scan_about.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Secure Restore


Secure Restore allows you to check restore points for malware activity before restoring the machine to the production environment. To scan restore points, Veeam Backup & Replication uses the following engines:

* Veeam Threat Hunter — a signature-based scan engine. For more information, see [Veeam Threat Hunter for Secure Restore](secure_restore_veeam_threat_hunter.md).
* 3rd party antivirus software. For more information, see [Antivirus Scan for Secure Restore](secure_restore_antivirus.md).
* YARA — a rule-based scan engine. For more information, see [YARA Scan for Secure Restore](secure_restore_yara.md).

To perform Secure Restore, see [Performing Secure Restore](malware_detection_secure_restore_console.md).

Supported Scenarios

Secure Restore is available for the following operations:

* Instant Recovery
* Instant Disk Recovery
* Virtual Disks Restore
* Entire VM Restore
* Restore to Microsoft Azure
* Restore to Amazon EC2
* Restore to Google Compute Engine
* Disk Export

Consider the following:

* You can perform Secure Restore for Microsoft Windows and Linux machines.

* Veeam Backup & Replication does not perform a malware scan for disks or volumes that cannot be mounted to the mount server. For example, Storage Spaces disks or ReFS volumes (if ReFS is not supported by the mount server OS) are skipped from the scan and restored in a regular way.

In This Section

* [How Secure Restore Works](malware_detection_secure_restore_hiw.md)
* [Veeam Threat Hunter for Secure Restore](secure_restore_veeam_threat_hunter.md)
* [Antivirus Scan for Secure Restore](secure_restore_antivirus.md)
* [YARA Scan for Secure Restore](secure_restore_yara.md)

Page updated 2026-07-24

