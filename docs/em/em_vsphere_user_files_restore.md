---
title: "em_vsphere_user_files_restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_vsphere_user_files_restore.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

The Files tab of vSphere Self-Service Backup Portal allows you to browse the guest OS file system in a VM backup and restore individual files. You can restore files from indexed and non-indexed guest OS file systems.

To restore guest OS files, follow the steps described in [Performing 1-Click File Restore](performing_1-click_file_restore.md).

|  |
| --- |
| Note |
| * When you restore from non-indexed guest OS file system, mount operation is performed using mount server associated with the backup repository that stores the backup file. * Before you restore files from a non-Windows VM, make sure that a helper host or helper appliance is configured on the backup server. For more information, see [Preparing for File Search and Restore (non-Windows machines)](em_preparing_for_linux_guest_file.md). |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
