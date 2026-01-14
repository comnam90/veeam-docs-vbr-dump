---
title: "Performing Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_perform_backup.html"
last_updated: "9/18/2025"
product_version: "13.0.1.1071"
---

# Performing Backup

In this article

To produce backups, Veeam Backup for Microsoft Entra ID runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup for Microsoft Entra ID supports two types of backup jobs:

* Tenant backup jobs that protect tenant data, such as users, groups, administrative units, roles, applications and conditional access policies.
* Log jobs that protect tenant audit and sign-in logs.

One backup job can protect data or logs of only one tenant. You can instruct Veeam Backup for Microsoft Entra ID to run jobs automatically according to a specified schedule or start them manually.

In This Section

* [Creating Tenant Backup Jobs](entra_id_backup_job.md)
* [Creating Log Backup Jobs](entra_id_log_job.md)
* [Managing Backup Jobs](entra_id_manage_jobs.md)

Page updated 9/18/2025

Page content applies to build 13.0.1.1071
