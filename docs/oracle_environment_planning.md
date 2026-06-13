---
title: "Oracle Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_environment_planning.html"
last_updated: "6/10/2026"
product_version: "13.0.2.29"
---

# Oracle Environment Planning


Before you deploy Veeam Plug-In, consider the following requirements and limitations.

Data Channel Allocation

Oracle Standard Edition supports only one data channel. Oracle Enterprise Edition supports multiple parallel channels. You can configure parallel channels in the Veeam Plug-In configuration wizard or by using the ALLOCATE CHANNEL command in RMAN scripts. For more information, see [Configuring Veeam Plug-In for Oracle RMAN](configuring_rman_plugin.md) or [Oracle RMAN Channel Allocation](rman_allocation_backup.md).

Installation Prerequisites

On machines running Linux or Unix OS, consider the following prerequisites:

* Before you install Veeam Plug-In, make sure that the /opt/veeam directory is writable.
* Before you configure Veeam Plug-In, make sure that the NOEXEC mount option is disabled for the /var and /tmp directories.

Scheduling

You can schedule backup processes with all Oracle RMAN relevant scheduling options like Cron, Windows Task Scheduler, UC4 and TWS.

If you use Veeam Backup & Replication or Veeam Agents to create image-level backups of the Oracle server, you can schedule the backup job and run Oracle RMAN backup scripts along with the backup job. For detailed instructions on how to add Oracle RMAN scripts to a backup job, see one of the following guides:

* For Veeam Backup & Replication: [Pre-Freeze and Post-Thaw Scripts](backup_job_vss_scripts_vm.md).
* For Veeam Agent for Windows: [Pre-Freeze and Post-Thaw Scripts](https://helpcenter.veeam.com/docs/agentforwindows/userguide/backup_job_vss_scripts.html?ver=60) section of the Veeam Agent for Windows User Guide.
* For Veeam Agent for Linux: [Pre-Freeze and Post-Thaw Scripts](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_script.html?ver=60#snapshot) section of the Veeam Agent for Linux User Guide.

|  |
| --- |
| Note |
| If you want to use Oracle RMAN scripts within backup jobs of Veeam Backup & Replication or Veeam Agents, consider the following:   * A backup job does not control the workflow of Oracle RMAN scripts. The backup job invokes the script and gets an exit status when the script is finished. Backup job logs show if the script was executed successfully. The script is considered to be executed successfully if the return is "0". To see if the script failed, configure the script to return the exit status different than "0" in case of any errors. * The default timeout for a custom script in a backup job is 10 minutes. If the script runs longer than the default time, consider submitting a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html). |

Oracle Temporary Tablespace

Veeam Plug-In runs SQL queries on the Oracle database to collect statistical information about the RMAN job processes. Based on availability of hardware resources, the Oracle server uses an allocated Oracle Temporary Tablespace to store the SQL queries.

To avoid lack of storage in the temporary tablespace, configure the Oracle Temporary Tablespace resources. For more information about creating and managing tablespaces, see [this Oracle article](https://docs.oracle.com/cd/A97630_01/server.920/a96540/statements_75a.htm).


