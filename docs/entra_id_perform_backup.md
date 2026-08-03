---
title: "Performing Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_perform_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup


To produce backups, Veeam Backup for Microsoft Entra ID runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup for Microsoft Entra ID supports two types of backup jobs:

* Tenant backup jobs that protect tenant data such as users, groups, administrative units, roles, conditional access policies, intune policies, contacts, devices, applications and service principals.
* Log jobs that protect tenant audit and sign-in logs.

One backup job can protect data or logs of only one tenant. You can instruct Veeam Backup for Microsoft Entra ID to run jobs automatically according to a specified schedule or start them manually.

|  |
| --- |
| Note |
| Microsoft Entra ID applications are referred to as application registrations in Microsoft Entra admin center. However, since Veeam Backup for Microsoft Entra ID uses the Microsoft Graph terminology, 'application registrations' are referred to as applications in this guide. The same applies to 'enterprise applications' that are referred to as service principals.  For more information on application and service principal objects in Microsoft Entra ID, see [Microsoft Docs](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals?tabs=browser). |

In This Section

* [Creating Tenant Backup Jobs](entra_id_backup_job.md)
* [Creating Log Backup Jobs](entra_id_log_job.md)
* [Managing Backup Jobs](entra_id_manage_jobs.md)

Page updated 2026-06-16

