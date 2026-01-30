---
title: "Pre-Freeze and Post-Thaw Scripts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vss_scripts_vm.html"
last_updated: "12/9/2025"
product_version: "13.0.1.1071"
---

# Pre-Freeze and Post-Thaw Scripts


If you plan to back up VMs running applications that do not support VSS, you can specify what scripts Veeam Backup & Replication must use to quiesce the VM. The pre-freeze script quiesces the VM file system and application data to bring the VM to a consistent state before Veeam Backup & Replication triggers a VM snapshot. After the VM snapshot is created, the post-thaw script brings the VM and applications to their initial state.

To specify pre-freeze and post-thaw scripts for the job, do the following:

1. Switch to the Scripts tab.
2. In the Script processing mode section, specify the scenario for scripts execution:

+ Select Require successful script execution if you want Veeam Backup & Replication to stop the backup process if the script fails.
+ Select Ignore script execution failures if you want to continue the backup process, even if script errors occur.
+ Select Disable script execution if you do not want to run scripts for the VM.

1. In the Windows scripts section, specify paths to pre-freeze and post-thaw scripts for Microsoft Windows VMs. For the list of supported script formats, see [Pre-Freeze and Post-Thaw Scripts](pre_post_scripts.md).
2. In the Linux scripts section, specify paths to pre-freeze and post-thaw scripts for Linux VMs. For the list of supported script formats, see [Pre-Freeze and Post-Thaw Scripts](pre_post_scripts.md).

If you have added a VM container with Microsoft Windows and Linux VMs to the job, you can select to execute both Microsoft Windows and Linux scripts for the VM container. When the job starts, Veeam Backup & Replication will automatically determine what OS type is installed on the VM and use the required scripts to quiesce this VM.

|  |
| --- |
| Tip |
| Besides pre-freeze and post-thaw scripts for VM quiescence, you can instruct Veeam Backup & Replication to run custom scripts before the job starts and after the job completes. For more information, see [Script Settings](backup_job_advanced_scripts_vm.md). |

![Pre-Freeze and Post-Thaw Scripts](images/vm_backup_job_vss_pre-post.webp)


