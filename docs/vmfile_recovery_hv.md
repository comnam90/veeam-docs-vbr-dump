---
title: "VM Files Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vmfile_recovery_hv.html"
last_updated: "3/24/2025"
product_version: "13.0.1.1071"
---

# VM Files Restore

In this article

You can restore specific VM files (.XML, .VMCX, .VMRS, .VMGS, .VHD, .VHDX) if any of these files are deleted or the volume is corrupted. This option provides a great alternative to entire VM restore, for example, when your VM configuration file is missing and you need to restore it. Instead of restoring the whole VM image to the production storage, you can restore a specific VM file only.

When you perform VM file restore, VM files are restored directly from regular image-level backups, without prior de-staging of VM images from backups. VM files can be restored to the original VM location or to a new location. The restored .VHD and .VHDX disk files preserve the original disk types (fixed or dynamic).

|  |
| --- |
| Note |
| If you recover a .VMCX file and further import a VM from it to Microsoft Hyper-V, the VM will be registered under the Veeam Recovery Checkpoint-(<GUID>) name. After import, you can rename the VM if required. |

Related Topics

[Restoring VM Files](performing_vmfile_restore.md)

Page updated 3/24/2025

Page content applies to build 13.0.1.1071
