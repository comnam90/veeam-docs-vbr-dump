---
title: "Exploring Non-Application Enabled Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_exploring_nonvss.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Exploring Non-Application Enabled Backups

In this article

If a backup file that you are exploring has been created without application-aware image processing in Veeam Backup & Replication, you can perform heuristic analysis to restore your Oracle data. The heuristic analysis mounts the required restore points and finds existing Oracle databases in these points.

The heuristic analysis enables you to restore your Oracle data even if the VM is powered-off or a database is shut-down at the time of backup. Note that if you backup a powered-on VM with a shut-down database, application-aware processing must be disabled in the backup job settings. With application-aware processing enabled, you can only backup databases in the OPEN state.

|  |
| --- |
| Note |
| The heuristic analysis requires a staging Oracle server to be configured in advance. For more information, see [Configuring Staging Oracle Server](veor_staging_server.md). |

To explore backups created without application-aware image processing, do the following:

1. [Launch the Heuristic Analysis wizard](nonvss_restore_wizard.md).
2. [Specify the target server](nonvss_target_server.md).
3. [Specify heuristic settings](nonvss_heuristic.md).

Page updated 3/27/2025

Page content applies to build 13.0.1.1071
