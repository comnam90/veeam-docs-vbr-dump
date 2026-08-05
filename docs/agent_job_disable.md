---
title: "Enabling and Disabling Veeam Agent Backup Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_disable.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Enabling and Disabling Veeam Agent Backup Job


You can temporary disable Veeam Agent backup jobs configured in Veeam Backup & Replication. When you disable a job, Veeam Backup & Replication does not start the job by the specified schedule. You can start a disabled job manually at any time you need. You can also enable a disabled job at any time.

You can enable or disable a Veeam Agent backup job in one of the following ways:

* [Using Veeam Backup & Replication Console](#console)
* [Using Veeam Backup & Replication Web UI](#webui)

Enabling and Disabling Veeam Agent Backup Job Using Veeam Backup & Replication Console

To disable a job:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the job and click Disable on the ribbon or right-click the job and select Disable.

To enable a disabled job, select it in the list and click Disable on the ribbon once again.

[![Disable Backup Job](images/agent_job_disable.webp)](images/agent_job_disable.webp "Disable Backup Job")

Enabling and Disabling Veeam Agent Backup Job Using Veeam Backup & Replication Web UI

To disable a job:

1. In the management pane, click Jobs.
2. Select the check box next to the necessary backup job, and from the Manage drop-down list, select Disable. Alternatively, right-click the job and click Manage > Disable.

To enable a disabled job, select it and click Manage > Enable on the toolbar, or right-click the job and click Manage > Enable.

[![Disable Backup Job](images/agent_job_disable_web.webp)](images/agent_job_disable_web.webp "Disable Backup Job")

Page updated 2026-07-28

