---
title: "Backup Job and Snapshot Script Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_guest_scripts_linux.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# Backup Job and Snapshot Script Settings


Before you configure script execution settings, review the considerations and limitations in the [Backup Job and Snapshot Scripts](agents_backup_linux_scripts.md) topic.

You can specify custom scripts that will be executed within the backup policy session on Linux computers. Veeam Agent for Linux supports the following types of scripts:

* Backup job scripts — pre-job and post-job scripts that run on the Veeam Agent computer before and after the backup policy session.
* Snapshot scripts — pre-freeze and post-thaw scripts that run on the Veeam Agent computer before and after the volume snapshot is created.

|  |
| --- |
| IMPORTANT |
| Snapshot script settings are not available if you select the Backup directly from live file system option at the [Backup Mode](agent_job_mode_linux.md) step of the wizard. If this option is selected, data will be backed up without a snapshot. |

Specifying Backup Job and Snapshot Scripts

To specify custom scripts for the policy:

1. At the Guest Processing step, select the Enable application-aware processing check box.
2. Click Applications.
3. In the displayed list, select a protection group or individual computer and click Edit.

To define custom settings for a computer added as a part of a protection group, you must include the computer to the list as a standalone object. To do this, click Add and choose the computer whose settings you want to customize. Then select the computer in the list and define the necessary settings.

1. [For an entire computer backup or volume-level backup policy] In the Processing Settings window, click the Scripts tab.
2. Select the Enable script execution check box.
3. In the Job scripts section, specify custom scripts that you want to execute before and after the backup policy session. To do this, in the Pre-job script and Post-job script fields, click Browse and choose executable files from a local folder on the backup server.
4. In the Snapshot scripts section, specify custom scripts that you want to execute before Veeam Agent for Linux creates a snapshot of the backed-up volume and after the snapshot is created. To do this, in the Pre-freeze script and Post-thaw script fields, click Browse and choose executable files from a local folder on the backup server.

When the backup policy is applied, Veeam Backup & Replication uploads the scripts to the /var/lib/veeam/scripts/<backup policy ID>/<script type>/ directory on each Veeam Agent computer included in the backup job. Veeam Agent executes the scripts from the same directory under the root user.

![Backup Job and Snapshot Script Settings](images/agent_policy_linux_scripts.webp)


