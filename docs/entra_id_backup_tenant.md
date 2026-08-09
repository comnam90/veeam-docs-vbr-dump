---
title: "Tenant Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/entra_id_backup_tenant.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Tenant Backup


To perform tenant backup, Veeam Backup for Microsoft Entra ID does the following:

1. Creates a Microsoft Entra ID repository on a dedicated PostgreSQL instance.
2. Reads the data from the backup scope of the tenant added to the backup job.
3. Transfers the data to the target repository and stores it as an encrypted database record.

Related Topics

[Creating Tenant Backup Jobs](entra_id_backup_job.md)

Page updated 2026-06-16

