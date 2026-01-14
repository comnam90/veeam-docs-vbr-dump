---
title: "Requirements and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/scan_backup_veeam_threat_hunter_limitations.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Requirements and Limitations

In this article

To get malware signature updates, a backup server and a mount server must have an internet connection. The following outgoing connections must be allowed:

* From the backup server to the Veeam License Update Server on ports 80 and 443. For more information, see [backup server connections](used_ports.md#backup).
* From the mount server to the Veeam Signature Update Server on port 443. For more information, see [mount server connections](used_ports.md#mount_server).

|  |
| --- |
| Note |
| Some files may not be scanned because of the file access problems caused by the conflict between Veeam Threat Hunter and third-party antivirus software. If you use Veeam Threat Hunter as a default scan engine, make sure that no third-party antivirus software is installed on the mount server. Alternatively, you can add exclusions for Veeam Backup & Replication to the third-party antivirus software configuration. For more details, see [this Veeam KB article](https://www.veeam.com/kb1999). |

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
