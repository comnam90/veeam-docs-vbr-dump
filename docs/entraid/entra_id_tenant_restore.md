---
title: "Tenant Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_tenant_restore.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Tenant Restore

In this article

In case a disaster strikes, you can use backups created by Veeam Backup for Microsoft Entra ID to restore the following tenant items and their properties: Microsoft Entra users, groups, roles, administrative units, applications, service principals and conditional access policies. Veeam Backup for Microsoft Entra ID allows you to restore tenant data to the original location only.

|  |
| --- |
| Important |
| To restore tenant data from a backup copy that is stored in a secondary backup repository, you must [retrieve the copied data](entra_id_tenant_restore_from_copy.md) first. |

To restore data of a protected Microsoft Entra tenant, do the following:

1. [Launch the Microsoft Entra ID Tenant Restore wizard](entra_id_restore_wizard_launch.md).
2. [Choose items to restore](entra_id_tenant_restore_items.md).
3. [Select a restore point](entra_id_tenant_restore_point.md).
4. [Connect to Microsoft Azure](entra_id_tenant_restore_logon.md).
5. [Specify restore options](entra_id_tenant_restore_options.md).
6. [Specify a restore reason](entra_id_tenant_restore_reason.md).
7. [Finish working with the wizard](entra_id_tenant_restore_finish.md).

Related Topics

[Appendix. Restoring Synchronized Users (Hybrid Identity)](entra_id_restore_sync_users.md)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
