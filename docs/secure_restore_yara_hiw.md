---
title: "How YARA Scan Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/secure_restore_yara_hiw.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# How YARA Scan Works


During the secure restore, the YARA scan works in the following way:

1. On the mount server, Veeam Backup & Replication runs the Veeam Mount Service to perform the following steps:

1. Mount machine disks from backups to the mount server under the C:\VeeamFLR\<machinename> folder (for Veeam Backup & Replication on Microsoft Windows) or the /tmp/Veeam.Mount.FS/<UUID>/ directory (for Veeam Backup & Replication on Linux).
2. Initiate a new scan session.

1. If malware activity is not detected, Veeam Backup & Replication will restore the machine or its disks to the target location. The malware detection event will not be created.
2. If malware activity is detected, Veeam Backup & Replication will perform the following steps:

1. Abort the restore process or restore the machine or its disks with restrictions depending on secure restore settings.

1. Create the malware detection event and mark objects as Infected.

If you do not want to create a malware detection event for a YARA rule, you can add a SuppressMalwareDetectionNotification tag to the name of the rule. For example:

|  |
| --- |
| rule SearchFileHash : SuppressMalwareDetectionNotification |

In this case, the malware detection event will not be created but the restore session will be finished with the Warning status.


