---
title: "Backup Job and Snapshot Scripts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_guest_scripts.html"
last_updated: "11/17/2025"
product_version: "13.0.1.1071"
---

# Backup Job and Snapshot Scripts


You can specify custom scripts that will be executed within the backup job session on Linux computers. Veeam Agent for Linux supports the following types of scripts:

* Backup job scripts — pre-job and post-job scripts that run on the Veeam Agent computer before and after the backup job session.
* Snapshot scripts — pre-freeze and post-thaw scripts that run on the Veeam Agent computer before and after the volume snapshot is created.

To learn more about requirements for scripts, see [Backup Job Scripts](agents_backup_linux_scripts.md).

Veeam Backup & Replication offers 2 scenarios for specifying script settings:

* [Scenario 1. Specify backup job scripts and snapshot scripts](#jobandsnapshot).

You can specify both backup job scripts and snapshot scripts for the backup job if you did not select the Backup directly from live file system option at the [Backup Mode](agent_job_mode_linux.md) step of the wizard.

* [Scenario 2. Specify backup job scripts only](#onlyjob).

You can specify only backup job scripts that will be executed on Linux computers if you selected the Backup directly from live file system option at the [Backup Mode](agent_job_mode_linux.md) step of the wizard.

|  |
| --- |
| TIP |
| You can also specify custom scripts that will be executed on the backup server before and after the backup job session. To learn more, see [Script Settings](agent_advanced_scripts_linux.md). |

Specifying Backup Job and Snapshot Scripts

To specify custom scripts for the job:

1. At the Guest Processing step, select the Enable application-aware processing check box.
2. Click Applications.
3. In the displayed list, select a protection group or individual computer and click Edit.

To define custom settings for a computer added as a part of a protection group, you must include the computer to the list as a standalone object. To do this, click Add and choose the computer whose settings you want to customize. Then select the computer in the list and define the necessary settings.

1. [For an entire computer backup or volume-level backup job] In the Processing Settings window, click the Scripts tab.

|  |
| --- |
| NOTE |
| For a file-level backup job, application-aware processing and database processing options are not available, and no tabs are displayed in the Processing Settings window. |

1. Select the Enable script execution check box.
2. In the Job scripts section, specify custom scripts that you want to execute before and after the backup job session. To do this, in the Pre-job script and Post-job script fields, click Browse and choose executable files from a local folder on the backup server.
3. In the Snapshot scripts section, specify custom scripts that you want to execute before Veeam Agent for Linux creates a snapshot of the backed-up volume and after the snapshot is created. To do this, in the Pre-freeze script and Post-thaw script fields, click Browse and choose executable files from a local folder on the backup server.

Veeam Agent for Linux supports scripts in the SH file format. During the backup job session, Veeam Backup & Replication will upload the scripts to the /var/lib/veeam/scripts directory on each Veeam Agent computer added to the backup job and execute them on these computers.

![Backup Job and Snapshot Scripts](images/agent_job_linux_scripts.webp)

Specifying Backup Job Scripts

To specify custom scripts for the job:

1. At the Guest Processing step, select the Enable application-aware processing check box.
2. Click Applications.
3. In the displayed list, select a protection group or individual computer and click Edit.

To define custom settings for a computer added as a part of a protection group, you must include the computer to the list as a standalone object. To do this, click Add and choose the computer whose settings you want to customize. Then select the computer in the list and define the necessary settings.

1. In the Processing Settings window, select the Enable script execution check box.
2. In the Pre-job script and Post-job script fields, click Browse to choose executable files from a local folder on the backup server.

Veeam Agent for Linux supports scripts in the SH file format. During the backup job session, Veeam Backup & Replication will upload the scripts to the /var/lib/veeam/scripts directory on each Veeam Agent computer added to the job and execute them on these computers.

![Backup Job and Snapshot Scripts](images/agent_job_linux_scripts_job.webp)


