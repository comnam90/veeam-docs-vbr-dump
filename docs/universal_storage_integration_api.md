---
title: "Universal Storage API Integrated Systems"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/universal_storage_integration_api.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Universal Storage API Integrated Systems

In this article

Storage vendors can leverage the Veeam Universal Storage API framework to integrate their storage solutions with Veeam Backup & Replication. With this kind of integration, you can use snapshots of Universal Storage API integrated systems to perform backup and restore operations.

Supported Storage Systems

The supported built-in storage systems are listed in section [System Requirements](storage_system_requirements.md#usais).

Supported Integration Types

You can add different storage systems to your infrastructure depending on the integration type you use. To learn which storage systems are supported for which integrations, see [System Requirements](storage_system_requirements.md).

Configuring Universal Storage API Integrated Systems

To start working with Universal Storage API integrated systems, you must perform the following steps:

1. Before adding a storage system to the backup infrastructure, check [Planning and Preparation](storage_limitations.md). If you plan to work with secondary storage arrays, you must add them to the backup infrastructure as well.
2. [[For Linux-based backup server] Install the storage system plug-in](storage_install_plugin_linux.md).
3. [[For Microsoft Windows-based backup server] Install the storage system plug-in](storage_install_plugin.md).
4. [Configure the infrastructure for storage integration](storage_infrastructure.md).
5. [Add Universal Storage API integrated system](usais_add.md).

|  |
| --- |
| Tip |
| For information on how to add built-in storage systems, see [Built-In Storage Systems](storage_configure_add_storage.md). |

In This Section

* [Installing and Updating Plug-ins on Linux-Based Backup Server](storage_install_plugin_linux.md)
* [Installing Plug-ins on Microsoft Windows-Based Backup Server](storage_install_plugin.md)
* [Adding Universal Storage API Integrated Systems](usais_add.md)
* [Update Notifications on Microsoft Windows-Based Backup Server](plug-in_update.md)
* [Uninstalling Plug-Ins from Microsoft Windows-Based Backup Server](storage_remove_plugin.md)
* [Uninstalling Plug-Ins from Linux-Based Backup Server](storage_remove_plugin_lin.md)

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
