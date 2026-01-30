---
title: "Requirements and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/scan_backup_antivirus_limitations.html"
last_updated: "7/8/2025"
product_version: "13.0.1.1071"
---

# Requirements and Limitations


The antivirus scan has the following requirements and limitations:

* The antivirus software must be installed on the mount server and support the command line interface (CLI).
* The antivirus configuration file must be located on the mount server and properly configured. For details, see [Antivirus Configuration File](av_scan_xml.md).

|  |
| --- |
| Note |
| If the antivirus is not installed or the configuration file is improperly configured, the Scan Backup session will fail. |

* For ESET NOD32 Antivirus version 9 and earlier, the Continue scanning all remaining files after the first occurrence option is supported with limitations. If the option is not selected, the antivirus scan will continue for the volume where malware activity was detected. Other volumes will not be scanned.

* If you install several antivirus software on the mount server, the Scan Backup session may fail because of the antivirus conflict and file access problems. To avoid such issues, use only one antivirus software.


