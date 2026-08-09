---
title: "Adding File Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/adding_managed_server_file_share.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding File Server


Before you add a Windows- or Linux-managed server as a file server to the inventory of the virtual infrastructure, consider the following:

* This server must meet requirements listed in the [Platform Support](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html?ver=13#unstructured-data) section.
* You must have this server added in Backup Infrastructure.

For more information on how to add servers, see the [Adding Microsoft Windows Servers](https://helpcenter.veeam.com/docs/vbr/userguide/add_windows_server.html?ver=13) and [Adding Linux Servers](https://helpcenter.veeam.com/docs/vbr/userguide/add_linux_server.html?ver=13) section.

* If you plan to use a dedicated [cache repository](https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup_infrastructure.html?ver=13#cache-repository), make sure it is added in Backup Infrastructure.
* Data from managed servers is transferred directly to the repository without a proxy server.

You can add the file server in one of the following ways:

* [Add a file server using console](adding_file_server_console.md).
* [Add a file server using web UI](adding_file_server_using_web_ui.md).

Page updated 2026-07-22

