---
title: "Veeam Data Mover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_transport_service.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Veeam Data Mover


Veeam Data Mover is a component that performs data processing tasks on behalf of Veeam Backup & Replication, such as retrieving source machine data, performing data deduplication and compression, and storing backed-up data on the target storage.

Veeam Data Mover can be persistent or non-persistent. When Veeam Data Mover is persistent, it is a part of [Veeam Transport Service](services_and_components.md) (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).

Depending on where and for which scenarios Veeam Data Mover is used, it can be persistent or non-persistent:

* For Microsoft Windows servers, Veeam Data Movers are persistent, that is, Veeam Data Mover is uploaded and installed on a server only once.

Veeam Backup & Replication automatically installs Veeam Data Mover when you [add a Microsoft Windows server](add_windows_server.md) to the backup infrastructure.

* For Linux servers, Veeam Data Movers can be persistent or non-persistent:

* Non-persistent Veeam Data Mover is uploaded and removed through the SSH connection each time Veeam Backup & Replication addresses a server. Veeam Backup & Replication uses non-persistent Veeam Data Movers for guest OS file restore and for guest processing when the [Use persistent guest agent](backup_job_vss_application_vm.md) option is disabled.
* Persistent Veeam Data Mover is uploaded and installed when you [add a Linux server](add_linux_server.md) to the backup infrastructure.

Requirements and Limitations for Veeam Data Movers

Before you use Veeam Data Movers, consider the following requirements and limitations:

* For Microsoft Hyper-V and Microsoft Windows servers:

* File and printer sharing must be enabled in the network connection settings of the added server.
* Make sure the user account that you use to add a Microsoft Windows server is in the local administrators group on the server being added.

* For Linux servers:

* Linux server version must be 64-bit. For more information, see [System Requirements](system_requirements.md).
* Make sure the user account that you use to add a Linux server has the [required permissions](required_permissions.md).

For a hardened repository, when you add a Linux server with single-use credentials, the user account must have elevated to root permission in order for Veeam Data Movers to be persistent. For more information, see [Specify Server Settings](hardened_repository_add_console_server.md).

|  |
| --- |
| Tip |
| If Veeam Data Mover on a Linux server fails for some reason, you can re-install it manually. For more information, see [this Veeam KB article](https://www.veeam.com/kb4298). |


