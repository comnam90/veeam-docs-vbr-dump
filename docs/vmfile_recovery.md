---
title: "VM Files Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vmfile_recovery.html"
last_updated: "3/24/2025"
product_version: "13.0.1.1071"
---

# VM Files Restore

In this article

You can restore specific VM files (.VMX, .VMXF, .NVRAM, .VMDK including flat files) if any of these files are deleted or the datastore is corrupted. This option provides a great alternative to entire VM restore, for example, when your VM configuration file is missing and you need to restore it. Instead of restoring the whole VM image to the production storage, you can restore a specific VM file only.

When you perform VM file restore, VM files are restored directly from regular image-level backups, without prior de-staging of VM images from backups. VM files can be restored to the original VM location or to a new location.

Related Topics

[Restoring VM Files](performing_vmfile_restore.md)

Page updated 3/24/2025

Page content applies to build 13.0.1.1071
