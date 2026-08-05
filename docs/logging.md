---
title: "Managing Logs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/logging.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Logs


Veeam Backup & Replication provides detailed logging of performed activities, data protection and disaster recovery tasks.

Logs are stored on the backup server and all servers added to the backup infrastructure:

* On Microsoft Windows-based backup server logs are stored in the following folders:

* Installation and upgrade logs - the %ProgramData%\Veeam\Setup\Temp folder.
* Logs for jobs, components and services - the %ProgramData%\Veeam\Backup folder. Veeam Backup & Replication creates separate folders for jobs and also separate log files or folders for components and services.
* Logs for PowerShell cmdlets - the %UserProfile%\AppData\Local\Veeam\Backup\VeeamPowerShell.log file.

* On Linux-based backup servers logs are stored in the following directories:

* Veeam Backup & Replication logs - the /var/log/VeeamBackup directory. With a clean installation of version 13.1 (build 13.1.0.411), backup service logs are created in the /var/lib/veeam/VeeamBackupLogFolder directory instead. The log location remains unchanged for upgrades to version 13.1.
* Veeam Updater logs - the /var/log/veeam directory.
* System logs - the /var/log directory.

|  |
| --- |
| Note |
| For a clean installation of Veeam Backup & Replication 13.1 (build 13.1.0.411), the layout of the /var/log directory has changed, and this directory now has a maximum size of 50 GB. Upgrades to version 13.1 keep the existing /var/log layout. |

* Logs for the Veeam Backup & Replication console and other user specific logs - the %UserProfile%\AppData\Local\Veeam\Backup folder on the machine where the console is installed.

* On Linux servers and ESXi hosts, logs are stored in the /var/log/VeeamBackup or /tmp/VeeamBackup directory.
* On Microsoft Windows servers and Hyper‑V hosts, logs are stored in the %ProgramData%\Veeam\Backup folder.

|  |
| --- |
| Tip |
| You can change default log files settings, for example, logs location and size. For more information, see [this Veeam KB article](https://www.veeam.com/kb1825). |

To collect log files from the backup server and servers managed by Veeam Backup & Replication, use the Export Logs wizard or the web UI as described in section [Exporting Logs](exporting_logs.md).

Page updated 2026-07-29

