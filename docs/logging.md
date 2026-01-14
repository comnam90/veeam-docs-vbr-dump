---
title: "Managing Logs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/logging.html"
last_updated: "2/24/2025"
product_version: "13.0.1.1071"
---

# Managing Logs

In this article

Veeam Backup & Replication provides detailed logging of performed activities, data protection and disaster recovery tasks.

Logs are stored on the backup server and all servers added to the backup infrastructure:

* On the backup server logs are stored in the following folders:

+ Installation and upgrade logs - the %ProgramData%\Veeam\Setup\Temp folder.
+ Logs for the Veeam Backup & Replication console and other user specific logs - the %UserProfile%\AppData\Local\Veeam\Backup folder.
+ Logs for jobs, components and services - the %ProgramData%\Veeam\Backup folder. Veeam Backup & Replication creates separate folders for jobs and also separate log files or folders for components and services.
+ Logs for PowerShell cmdlets - the %UserProfile%\AppData\Local\Veeam\Backup\VeeamPowerShell.log file.

* On Linux servers and ESXi hosts, logs are stored in the /var/log/VeeamBackup or /tmp/VeeamBackup directory.
* On Microsoft Windows servers and Hyper‑V hosts, logs are stored in the %ProgramData%\Veeam\Backup folder.

|  |
| --- |
| Tip |
| You can change default log files settings, for example, logs location and size. For more information, see [this Veeam KB article](https://www.veeam.com/kb1825). |

To collect log files from the backup server and servers managed by Veeam Backup & Replication, use the Export Logs wizard as described in section [Exporting Logs](exporting_logs.md).

Page updated 2/24/2025

Page content applies to build 13.0.1.1071
