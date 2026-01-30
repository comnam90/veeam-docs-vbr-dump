---
title: "How Database Data Encryption Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encryption_database_hiw.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---

# How Database Data Encryption Works


To protect data encryption keys, passwords, secret keys, KMS keys, certificates and other sensitive information stored in the configuration database, Veeam Backup & Replication uses built-in operating system mechanisms for data protection:

* Veeam Backup & Replication on Linux uses ASP.NET Core. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/aspnet/core/security/data-protection/introduction?view=aspnetcore-9.0).
* Veeam Backup & Replication on Microsoft Windows uses Data Protection API (DPAPI). For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/previous-versions/ms995355%28v%3Dmsdn.10%29).

For encrypted configuration backups, data protection on the operating system level is replaced with data protection mechanisms provided by Veeam Backup & Replication. For more information, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md).


