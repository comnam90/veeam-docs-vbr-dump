---
title: "How Antivirus Scan Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/scan_backup_antivirus_hiw.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# How Antivirus Scan Works


During the Scan Backup session, the antivirus scan works in the following way:

1. On the mount server, Veeam Backup & Replication runs the Veeam Mount Service to perform the following steps:

1. Mount machine disks from backups to the mount server under the C:\VeeamFLR\<machinename> folder (for Veeam Backup & Replication on Microsoft Windows) or the /run/media/Veeam.Mount.FS/<id> directory (for Veeam Backup & Replication on Linux).
2. Initiate an antivirus scan.

1. If the antivirus does not find a clean restore point, the Scan Backup session will be finished with the Failed status. The malware detection event will be created for each restore point. Objects will be marked as Infected.
2. If the antivirus finds a clean restore point, the Scan Backup session will be finished with the Success status. The malware detection event will not be created.

![How Antivirus Scan Works](images/av_scan_hiw.webp)


