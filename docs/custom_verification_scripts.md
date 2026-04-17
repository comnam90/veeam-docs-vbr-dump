---
title: "Custom Verification Scripts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/custom_verification_scripts.html"
last_updated: "4/14/2026"
product_version: "13.0.1.2067"
---

# Custom Verification Scripts


Veeam Backup & Replication allows you to verify machines with custom verification scripts.  Scripts are executed on the backup server side and support the following file types:

* [For Veeam Backup & Replication on Windows] Programs (.exe, .bat, .cmd), Windows Script files (.js, .vbs, .wsf), and PowerShell files (.ps1).
* [For Veeam Backup & Replication on Linux] PowerShell files (.ps1) and Bash Shell Script files (.sh).

|  |
| --- |
| Important |
| Consider the following:   * Do not pass sensitive information using script arguments in a user interface. * Running scripts with user credentials is supported only for Veeam Backup & Replication on Window. For Veeam Backup & Replication on Linux, scripts always run under a local service account. * Scripts only run in an isolated environment — virtual lab. * [For Veeam Backup & Replication on Linux] Scripts cannot make calls to local IP addresses. * [For Veeam Backup & Replication on Linux] Scripts must be placed in /var/lib/veeam/scripts. You can upload scripts from the console using the Files view. |


