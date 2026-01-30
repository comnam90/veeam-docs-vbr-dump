---
title: "Configuring Veeam Backup for Microsoft Entra ID"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_configuration.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Configuring Veeam Backup for Microsoft Entra ID


To start working with Veeam Backup for Microsoft Entra ID, perform the following steps for its configuration:

1. [Configure a cache repository](entra_id_configure_repo.md).
2. [Add to the backup infrastructure the Microsoft Entra ID tenant](entra_id_add_tenant.md) that you want to protect.
3. [Optional] [Configure remote Microsoft Entra ID backup repository](entra_id_manage_repo.md) where Veeam Backup for Microsoft Entra ID will store backups of Microsoft Entra ID tenants.
4. [Optional] [Configure the primary log backup repository](entra_id_configure_repo.md) where Veeam Backup for Microsoft Entra ID will store backups of audit logs and sign-in logs.
5. [Optional] [Configure the secondary log backup repositories](entra_id_configure_repo.md) where Veeam Backup for Microsoft Entra ID will store backups of audit logs and sign-in logs.
6. [Optional] Configure global email notification options to get notifications with results on jobs performed on the backup server. For more information, see the Veeam Backup & Replication User Guide, section [Configuring Global Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/general_email_notifications.html?ver=13).


