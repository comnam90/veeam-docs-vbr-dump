---
title: "Editing Veeam Agent Backup Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_edit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Veeam Agent Backup Job Settings


You can edit Veeam Agent backup jobs configured in Veeam Backup & Replication at any time. For example, you may want to edit a backup job to change the backup scope, target location or job scheduling settings.

|  |
| --- |
| NOTE |
| Consider the following:   * You cannot change the type of protected computers added to the job and the job mode (that is, change a Veeam Agent backup job to a backup policy and vice versa). * [For Veeam Agent backup jobs for Linux computers] You cannot change the backup mode from file-level to volume-level and vice versa. |

You can edit a Veeam Agent backup job in one of the following ways:

* [Using Veeam Backup & Replication Console](#console)
* [Using Veeam Backup & Replication Web UI](#webui)

Editing Veeam Agent Backup Job Settings Using Veeam Backup & Replication Console

To edit job settings:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the job and click Edit on the ribbon or right-click the job and select Edit.
4. Complete the steps of the Edit Agent Backup Job wizard to change the job settings as required.

[![Edit Backup Job](images/agent_backup_job_edit.webp)](images/agent_backup_job_edit.webp "Edit Backup Job")

Editing Veeam Agent Backup Job Settings Using Veeam Backup & Replication Web UI

To edit job settings:

1. In the management pane, click Jobs.
2. Select the check box next to the necessary backup job, and from the Manage drop-down list, select Edit. Alternatively, right-click the job and click Manage > Edit.
3. Complete the steps of the Edit Agent Backup Job wizard to change the job settings as required.

[![Edit Backup Job](images/agent_job_edit_web.webp)](images/agent_job_edit_web.webp "Edit Backup Job")

Page updated 2026-07-28

