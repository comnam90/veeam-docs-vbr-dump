---
title: "Backup Job and Snapshot Scripts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_windows_scripts.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Backup Job and Snapshot Scripts


You can instruct Veeam Agent to run custom scripts within the backup job session. Veeam Agent for Microsoft Windows supports the following types of scripts:

* [Pre-freeze and post-thaw scripts executed on the Veeam Agent computer](#snapshot)
* [Pre-job and post-job scripts executed on the Veeam backup server](#job_server) (for backup jobs managed by the backup server)

Considerations and Limitations

* Scripts must be created before you configure the backup job. You must specify paths to them in the backup job settings.

If you use Veeam Backup & Replication on Linux, you must place the scripts into the /var/lib/veeam/scripts/ directory on the backup server.

If you use Veeam Backup & Replication on Windows, you can place the script files in any local folder on the backup server.

* Veeam Agent supports scripts in the .EXE, .BAT,.CMD and .PS1 formats.
* Scripts must have Windows line endings (CRLF).
* Script settings are enabled at the backup job level. If you want to configure multiple backup jobs, you can specify individual scripts for each job.
* If you use relative paths in your scripts, during script execution such paths will refer to the root directory. For example, the script may have an output that must be saved to a new file. If you specify a relative path to that file or only a file name, the file will be created in the root directory. To specify a different location for a file, use a full absolute path.

Pre-Freeze and Post-Thaw Scripts

Veeam Agent runs these scripts before and after creating a snapshot of the backed-up volume. For example, the pre-freeze script may quiesce the file system and application data to bring the OS to a consistent state before Veeam Agent creates a snapshot. After the snapshot is created, the post-thaw script brings the file system and applications to their initial state.

You can specify pre-freeze and post-thaw script settings at the Guest Processing step of a backup job wizard. To learn more, see sections [Pre-Freeze and Post-Thaw Scripts](agent_job_vss_scripts.md) (for backup jobs managed by the backup server) and [Pre-Freeze and Post-Thaw Scripts](agent_policy_win_vss_scripts.md) (for backup policies).

During the backup job session, Veeam Backup & Replication uploads the scripts to each Veeam Agent computer added to the backup job and executes them on these computers. The scripts run in the same way as in the standalone version of Veeam Agent. To learn more, see the [Backup Job Scripts](https://helpcenter.veeam.com/docs/agentforwindows/userguide/pre_post_scripts.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.

Pre-Job and Post-Job Scripts

Veeam Agent runs these scripts before the backup job starts and after the backup job completes. You can use pre-job and post-job scripts, for example, to throttle activities of some resource-consuming services on the backup server during the backup process.

You can specify backup job script settings at the Storage step of the backup job wizard. To learn more, see [Script Settings](agent_job_advanced_scripts.md).

During the backup job session, Veeam Backup & Replication executes the scripts on the backup server under the account under which the Veeam Backup Service runs (the local System account or account that has the local Administrator permissions on the backup server).

Script Execution Order

If you specify both pre-job and post-job and pre-freeze and post-thaw scripts, the scripts will be executed in the following order:

1. Pre-job script
2. Pre-freeze script
3. Post-thaw script
4. Post-job script


