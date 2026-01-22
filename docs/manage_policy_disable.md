---
title: "Enabling and Disabling Backup Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/manage_policy_disable.html"
last_updated: "1/20/2026"
product_version: "13.0.1.1071"
---

# Enabling and Disabling Backup Policy


You can temporarily disable scheduled application backup policies configured in Veeam Backup & Replication. When you disable a job, Veeam Backup & Replication does not start the job by the specified schedule. You can start a disabled job manually at any time you need. You can also enable a disabled job at any time.

To disable an application backup policy:

1. Open the Home view.
2. In the inventory pane, select Jobs.
3. In the working area, select the application backup policy and click Disable on the ribbon or right-click the policy and select Disable.

If you disabled a backup policy in the Veeam Backup & Replication console, this backup policy will not start by schedule.

To enable a disabled policy, select it in the list and click Disable on the ribbon once again.

[![Disable Application Backup Policy](images/plugins_application_policy_disable.webp)](images/plugins_application_policy_disable.webp "Disable Application Backup Policy")


