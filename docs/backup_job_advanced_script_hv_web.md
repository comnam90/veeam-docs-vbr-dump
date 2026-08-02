---
title: "Script Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_advanced_script_hv_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Script Settings


To specify script settings for the backup job:

1. At the Storage step of the wizard, click Change default advanced settings next to the Advanced settings.
2. Click the Scripts tab.
3. If you want to execute custom scripts before and after the backup job, set the Run the following script before the job and Run the following script after the job toggles to On and specify paths to the executable files on the backup server. The scripts are executed on the backup server.

You can select to execute pre- and post-backup actions after a number of backup sessions or on specific week days.

* If you select the Run scripts every <N> backup session option, specify the number of the backup job sessions after which the scripts must be executed.
* If you select the Run scripts on the selected days only option, click Days and specify week days on which the scripts must be executed.

|  |
| --- |
| Note |
| Consider the following:   * Custom scripts you define in the advanced job settings relate to the backup job itself, not the VM quiescence process. To add pre-freeze and post-thaw scripts for VM image quiescence, use the Guest Processing step of the wizard.  * If you select the Run scripts on the selected days only option, Veeam Backup & Replication executes scripts only once on each selected day — when the job runs for the first time. During subsequent job runs, scripts are not executed.  * To run the script, Veeam Backup & Replication uses the service account under which the Veeam Backup Service is running. |

[![Specify script settings](images/hv_backup_job_settings_adv_web.webp)](images/hv_backup_job_settings_adv_web.webp "Specify script settings")

Page updated 2026-07-17

