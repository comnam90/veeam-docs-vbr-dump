---
title: "Managing Backup Job Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/job_details_permissions_hv_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Backup Job Permissions


You can specify who owns a backup job and who can access it. Use the Permissions tab to set the job owner and grant access to other users.

To open the Permissions tab:

1. Open the [Viewing Backup Job Details](realtime_statistics_hv_web.md) view for the job.
2. Click the Permissions tab.

Job Owner

The Job Owner box shows the user account that owns the job. To change the job owner:

1. Click Change next to the Job owner field.
2. Select the user account that will own the job. [TODO: confirm the exact selection dialog and whether you type or pick the account.]

Effective Access

The Effective Access box lists the users and groups that can access the job. If no entries are configured, the box shows No effective access entries.

To grant access:

1. Click Add.
2. Select the user or group to add to the list. [TODO: confirm the exact selection dialog and available fields.]

To revoke access, select an entry in the list and click Remove.

|  |
| --- |
| Note |
| [TODO: describe how effective access relates to roles assigned in Veeam Backup & Replication and link to the relevant RBAC topic.] |

[![Click to zoom in](images/backup_job_permissions.webp)](images/backup_job_permissions.webp "Click to zoom in")

Page updated 2026-06-16

