---
title: "Adding File Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/adding_managed_server_file_share.html"
last_updated: "3/18/2025"
product_version: "13.0.1.1071"
---

# Adding File Server

In this article

Before you add a Windows- or Linux-managed server as a file server to the inventory of the virtual infrastructure, consider the following:

* This server must meet requirements listed in the [Platform Support](https://helpcenter.veeam.com/docs/backup/vsphere/platform_support.html?ver=120#unstructured-data-backup-support) section.
* You must have this server added in Backup Infrastructure.

For more information on how to add servers, see the [Adding Microsoft Windows Servers](https://helpcenter.veeam.com/docs/backup/vsphere/add_windows_server.html?ver=120) and [Adding Linux Servers](https://helpcenter.veeam.com/docs/backup/vsphere/add_linux_server.html?ver=120) section.

* If you plan to use a dedicated [cache repository](https://helpcenter.veeam.com/docs/backup/vsphere/unstructured_data_backup_infrastructure.html?ver=120#cache_repository), make sure it is added in Backup Infrastructure.
* Data from managed servers is transferred directly to the repository without a proxy server.

To add a managed Windows or Linux server as a source of unstructured data, do the following:

1. [Launch the New File Server wizard](file_share_backup_managed_server_share_launch_wizard.md).
2. [Add the managed server as a file server](file_share_backup_managed_server_file_server.md).
3. [Specify file server processing settings](file_share_backup_managed_server_share_processing_settings.md).
4. [Review the components to be installed](file_share_backup_managed_server_share_review.md).
5. [Apply file server settings](file_share_backup_managed_server_share_apply.md).
6. [Finish working with the wizard](file_share_backup_managed_server_share_summary.md).

Page updated 3/18/2025

Page content applies to build 13.0.1.1071
