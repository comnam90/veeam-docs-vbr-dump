---
title: "Configuring Veeam Backup for Microsoft Azure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Veeam Backup for Microsoft Azure


To start working with Veeam Plug-in for Microsoft Azure, perform a number of steps for its configuration:

1. [Add backup appliances to the backup infrastructure](azure_appliances.md).
2. [Add repositories that will be used to store backed-up data](azure_repositories.md).

This step applies if you plan to protect Azure VMs, Azure SQL databases, Cosmos DB for PostgreSQL accounts or Cosmos DB for MongoDB accounts with backups, or to save additional copies of virtual network configuration backups to a repository.

1. Configure the added backup appliances:

1. [Add service accounts to get access to Azure services and resources](azure_accounts.md).
2. [[Optional] Add user accounts to control access to Veeam Backup for Microsoft Azure](azure_managing_permissions.md).
3. [[Optional] Configure worker instance settings](azure_workers.md).

If you do not configure settings for worker instances, backup appliances will use the default settings of Azure regions where worker instances will be launched.

1. [Configure policy templates that will be used by SLA-based backup policies](azure_sla_storage_manage.md).
2. [[Optional] Configure deployment, global retention, email notification and single sign-on settings](azure_general_settings.md).

|  |
| --- |
| Note |
| Even after you add accounts that manage your Azure resources and configure all the necessary settings, Veeam Plug-in for Microsoft Azure will populate neither the list of Azure VMs nor the list of Azure SQL databases nor the list of Cosmos DB accounts nor the list of Azure file shares on the [Resources](azure_viewing_resources.md) page — unless you create backup policies and specify regions where the Azure resources belong, as described in section [Performing Backup](azure_backup.md). |

Page updated 2026-07-01

