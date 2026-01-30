---
title: "Advanced Settings for Backup to Tape Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/advanced_advanced.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Advanced Settings for Backup to Tape Job


This step of the wizard is available if you selected a regular media pool at the Media Pool step of the wizard.

1. Select the Process latest full backup chain only check box if you want to copy only the last backup chain with each tape job run. The source backup chain consists of a full backup (active or synthetic) and subsequent increments. If you disable this option, the tape job will back up all restore points that are not on tape.
2. Select the Use hardware compression when available check box if the tape drive should compress data before writing it to tape.
3. Select the Run the following script before the job and Run the following script after the job check boxes and click Browse to choose executable files.

You can select to execute pre- and post-job actions after a number of job sessions or on specific week days.

* If you select the Run scripts every... backup session option, specify the number of the job sessions after which the scripts must be executed.
* If you select the Run scripts on selected days only option, click Days and specify week days on which the scripts must be executed.

![Advanced Settings for Backup to Tape Job](images/backup_to_tape_advanced_advanced.webp)

|  |
| --- |
| Tip |
| After you specify necessary settings for the tape job, you can save them as default settings. To do this, click Save as Default at the bottom left corner of the Advanced Settings window. When you create a new backup to tape job, Veeam Backup & Replication will automatically apply the default settings to the new job. |


