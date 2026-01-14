---
title: "How YARA Scan Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/scan_backup_yara_hiw.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# How YARA Scan Works

In this article

During the Scan Backup session, the YARA scan works in the following way:

1. On the mount server, Veeam Backup & Replication runs the Veeam Mount Service to perform the following steps:

1. Mount machine disks from backups to the mount server under the C:\VeeamFLR\<machinename> folder (for Veeam Backup & Replication on Microsoft Windows) or the /tmp/Veeam.Mount.FS/<UUID>/ directory (for Veeam Backup & Replication on Linux).
2. Initiate a new YARA scan.

1. If you search for the last clean restore point, consider the following:

1. If a clean restore point is found, the Scan Backup session will be finished with the Success status. The malware detection event will not be created.
2. If a clean restore point is not found, the Scan Backup session will be finished with the Failed status. The malware detection event will be created for each restore point. Objects will be marked as Infected.

If you do not want to create a malware detection event for a YARA rule, you can add a SuppressMalwareDetectionNotification tag to the name of the rule. For example:

|  |
| --- |
| rule SearchFileHash : SuppressMalwareDetectionNotification |

In this case, the malware detection event will not be created but the Scan Backup session will be finished with the Warning status.

1. If you check the restore point for sensitive data, consider the following:

1. If sensitive data is found, the Scan Backup session will be finished with the Failed status.
2. If sensitive data is not found, the Scan Backup session will be finished with the Success status.

In both cases, the malware detection event will not be created.

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
