---
title: "Protecting Virtual Network Configurations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_overview_vnet.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protecting Virtual Network Configurations


To protect Azure virtual network configurations, Veeam Plug-in for Microsoft Azure retrieves configuration data through API and saves this data to the configuration database. For more information on how virtual network configuration backup works, see [Virtual Network Configuration Backup](azure_how_vnet_backup_works.md).

How To Protect Virtual Network Configurations

To modify the virtual network configuration backup policy settings, perform the following steps:

1. [Check limitations and prerequisites](azure_limitations.md#backup).
2. [Specify service accounts to access Azure services and resources](azure_service_accounts.md).
3. [Add backup repositories to save additional virtual network configuration backup copies](azure_repositories.md).
4. [[Optional] Configure global retention settings for obsolete snapshots and session records](azure_configuring_global_retention.md).
5. [[Optional] Configure email notification settings for automated delivery of backup policy results and daily reports](azure_configuring_notification_settings.md).
6. [Complete the Edit Virtual Network Configuration Backup Policy wizard](azure_vnet_backup_edit.md).

Related Topics

[Virtual Network Configuration Restore](azure_vnet_restore_hiw.md)

Page updated 2026-07-01

