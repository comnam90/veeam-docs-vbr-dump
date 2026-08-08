---
title: "Viewing Backup Permissions Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_details_permissions_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Viewing Backup Permissions Using Web UI


On the Permissions tab, you can view who owns a backup job and who can access it.

To view backup permissions, do the following:

1. In the management pane, select the Backups node.
2. Select the backup, and click Permissions.

A backup inherits the Job Owner and Effective Access settings from the backup job that created it. While that job exists, you cannot edit these settings on the backup Permissions tab. To change them, use the [Permissions tab](job_details_permissions_web.md) of the backup job.

If you delete the job, the backup remains and you can edit the Job Owner and Effective Access settings on the backup Permissions tab.

Backup Owner

The Backup owner box shows the user account that owns the backup. To change the owner, do the following:

1. Click Change next to the Backup owner field.
2. Select the account that will own the backup.

Effective Access

By default, no users are granted access, and the Effective Access box shows No effective access entries. To grant access, do the following:

1. Click Add.
2. Select the user or group to add to the list.

To revoke access, select an entry in the list and click Remove.

[![Click to zoom in](images/backup_permissions_web.webp)](images/backup_permissions_web.webp "Click to zoom in")

Page updated 2026-08-04

