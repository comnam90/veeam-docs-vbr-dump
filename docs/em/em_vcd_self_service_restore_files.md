---
title: "em_vcd_self_service_restore_files"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_vcd_self_service_restore_files.html"
last_updated: "11/22/2024"
product_version: "13.0.1.1071"
---


In this article

Members of a VMware Cloud Director organization can browse the VM file system, search for specific files and restore them. As a source, you can use a VM backup or snapshot replica. Both indexed and non-indexed guest OS file systems are supported.

To restore guest OS files, open the the Files tab and follow the steps described in [Performing 1-Click File Restore](performing_1-click_file_restore.md).

|  |
| --- |
| Note |
| * When you restore from non-indexed guest OS file system, mount operation is performed using mount server associated with the backup repository that stores the backup file. * Before you restore files from a non-Windows VM, make sure that a helper host or helper appliance is configured on the backup server. For more information, see [Preparing for File Search and Restore (non-Windows machines)](em_preparing_for_linux_guest_file.md). |

Page updated 11/22/2024

Page content applies to build 13.0.1.1071
