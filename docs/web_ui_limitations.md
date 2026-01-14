---
title: "Veeam Backup & Replication Web UI Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/web_ui_limitations.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Veeam Backup & Replication Web UI Limitations

In this article

The Veeam Backup & Replication web UI has the following limitations:

* Backup jobs only for [VMware vSphere](backup_job_web.md) and [Microsoft Hyper-V](backup_job_hv_web.md) VMs are available in the Veeam Backup & Replication web UI.

Alternative: To manage backup jobs for other platforms, use the [Veeam Backup & Replication console](vbr_ui.md) instead.

* Guest OS file recovery to another location is not supported.

Alternative: To recover guest OS files to another location, use the [Veeam Backup & Replication console](performing_guest_restore.md) instead.

* For any supported operation, advanced settings available under Advanced in the Veeam Backup & Replication desktop application are not accessible in Veeam Backup & Replication web UI.

Alternative: Use the [Veeam Backup & Replication console](vbr_ui.md) instead.

* You cannot modify existing repository settings in the web UI.

Alternative: Use the [Veeam Backup & Replication console](backup_repository.md) instead.

* Transaction-log backup configuration is not supported in the web UI.

Alternative: Use the [Veeam Backup & Replication console](sql_backup_job.md) instead.

* Cross-platform restore operations (for example, Hyper-V to vSphere) are not available.

Alternative: Use the [Veeam Backup & Replication console](vm_recovery_all.md) instead.

* File-level restore is only possible to the original location.

Alternative: Use the [Veeam Backup & Replication console](guest_file_recovery.md) or [Veeam Backup Enterprise Manager](https://helpcenter.veeam.com/docs/vbr/em/em_backup_restore_app_items.html?ver=13) instead.

* The job wizard does not support configuring a secondary destination.

Alternative: Create a [backup copy job](backup_copy_create.md).

* The Install missing updates option in the Manage Updates group installs updates on Linux-based infrastructure components (Veeam Infrastructure Appliances), but not on the Linux-based backup server (Veeam Software Appliance). To update the backup server, use the [Veeam Updater](update_appliances.md).

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
