---
title: "How Veeam Threat Hunter Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/secure_restore_veeam_threat_hunter_hiw.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# How Veeam Threat Hunter Works


Veeam Threat Hunter is a signature-based scan engine provided by Veeam. It is used as an alternative to third-party antivirus software to scan the restore points. The Veeam Threat Hunter Service is automatically installed on a mount server and runs in the background.

During the restore session, the Veeam Threat Hunter scan works in the following way:

1. On the mount server, Veeam Backup & Replication runs the Veeam Mount Service to perform the following steps:

1. Mount machine disks from backups to the mount server under the C:\VeeamFLR\<machinename> folder (for Veeam Backup & Replication on Microsoft Windows) or the /tmp/Veeam.Mount.FS/<UUID>/ directory (for Veeam Backup & Replication on Linux).
2. Initiate a new scan session.

|  |
| --- |
| Note |
| Veeam Threat Hunter checks all disks simultaneously. |

1. If Veeam Threat Hunter does not detect malware activity, Veeam Backup & Replication will restore the machine or its disks to the target location. The malware detection event will not be created.
2. If Veeam Threat Hunter detects malware activity, Veeam Backup & Replication will perform the following steps:

1. Abort the restore process or restore the machine or its disks with restrictions depending on secure restore settings.

1. Create the malware detection event and mark objects as Infected.

|  |
| --- |
| Note |
| Consider the following:   * Veeam Threat Hunter checks updates for malware signatures before running the scan, but no more often than once an hour. Note that the initial malware signature update may take longer than the subsequent updates. * By default, Veeam Threat Hunter checks all files on disks. If you want to add exclusions, see [this Veeam KB article](https://www.veeam.com/kb4688). * If you deploy a new installation of Veeam Backup & Replication, Veeam Threat Hunter will be selected as a default scan engine in the malware detection settings. The Veeam Threat Hunter Service will be automatically installed on a mount server when you add it to the backup infrastructure. * If you upgrade to Veeam Backup & Replication 13.0.1 or later, the Veeam Threat Hunter Service will be automatically installed on a mount server after the upgrade. For backwards compatibility, third-party antivirus software will be selected as a default scan engine in the malware detection settings. |


