---
title: "Retention Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_retention.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Retention Policy


Veeam Plug-In allows you to configure retention policy for Microsoft SQL Server backups. The retention policy helps maintain the life cycle of restore points and make sure that backup files do not consume the entire space on the backup repository.

Veeam Plug-In for Microsoft SQL Server applies the retention policy at the database level and retains restore points for a number of days defined in the backup settings. After each full backup or differential backup session, Veeam Plug-In checks the time when restore points for the backed-up database were created and removes outdated restore points from the backup chain.

Veeam Plug-In does not remove outdated restore points immediately. Instead, Veeam Plug-In applies the retention policy to the inactive part of the backup chain — that is, the previous full backup and its dependent differential and log backups. Only after the last incremental backup in the chain becomes outdated, Veeam Plug-In will remove the inactive backup chain.

For example, the retention policy is set to 7 days. Veeam Plug-In is set to create full backups each Sunday, and differential backups and log backups are created Monday through Saturday. Although a new full backup is created on Sunday, the previous full backup is not deleted. Without the full backup, the functionality of the subsequent chain of differential and log backups will be compromised. Veeam Plug-In will wait for the time when the last restore point in the inactive backup chain becomes outdated, and only then will delete the entire inactive chain, which will happen next Saturday.

[![Retention Policy Backup Chain](images/plugins_mssql_retention.webp)](images/plugins_mssql_retention.webp "Retention Policy Backup Chain")

For more information, see [Configuring Retention Policy](plugins_mssql_retention_policy.md).


