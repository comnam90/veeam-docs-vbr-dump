---
title: "Protecting Tenant Data"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/overview_entra_id_tenant.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# Protecting Tenant Data


To produce backups of Microsoft Entra ID tenant data, Veeam Backup for Microsoft Entra ID runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup for Microsoft Entra ID does not install agent software to back up Microsoft Entra ID tenant data — it uses native Microsoft capabilities instead. During every backup session, Veeam Backup for Microsoft Entra ID creates a backup of the Microsoft Entra ID tenant added to a backup job.

How to Protect Microsoft Entra ID Tenant Data

To create a Microsoft Entra ID backup job, complete the following steps:

1. [Check limitations and prerequisites](entra_id_limitations.md).
2. [Configure log and cache repositories](entra_id_configure_repo.md).
3. [Add a Microsoft Entra ID tenant](entra_id_add_tenant.md).
4. [Connect to a remote Microsoft Entra ID repository, if necessary](entra_id_manage_repo.md).
5. [Complete the New Microsoft Entra ID Tenant Backup Job wizard](entra_id_backup_job.md).


