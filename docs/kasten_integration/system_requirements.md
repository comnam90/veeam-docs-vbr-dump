---
title: "system_requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/system_requirements.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---


In this article

Before you start using Veeam Plug-In for Kasten, consider the following:

Backup Server

The machine where the Veeam Kasten Plug-in for Veeam Backup & Replication will run must meet the system requirements described in the [System Requirements](https://helpcenter.veeam.com/docs/backup/vsphere/system_requirements.html?ver=120) section in the Veeam Backup & Replication User Guide.

Additionally, the following software must be installed:

* Microsoft .NET Core Runtime 8.0
* Microsoft ASP.NET Core Shared Framework 8.0

|  |
| --- |
| Important |
| Microsoft ASP.NET Core Shared Framework and Microsoft .NET Core Runtime must be of the same version (up to the minor version number).  For example, if the version of Microsoft ASP.NET Core Shared Framework is 8.0.8, then the version of Microsoft .NET Core Runtime must also be 8.0.8. |

Starting from version 6.5.9, Veeam Plug-In for Kasten no longer supports Veeam Backup & Replication installed on Microsoft Windows Server 2012 and 2012 R2.

Kubernetes Distribution Requirements

Veeam Plug-In for Kasten supports only backup exports of Kubernetes persistent volumes to Veeam backup repositories. For details on which volumes are supported for export to a VBR repository, see [Veeam Kasten Docs](https://docs.kasten.io/latest/install/storage/#vbr-integration).

Kasten Application Version

A Veeam Kasten application must be the 5.5.3 version or higher.

Kasten Dashboard Access

An external access to the Kasten dashboard must be set up. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/access/dashboard.html).

Veeam Backup & Replication

Veeam Plug-In for Kasten version 13.2.1.60 supports integration with Veeam Backup & Replication version 13.01.

Veeam Backup Repositories Requirements

Veeam backup repositories, where you want to keep backups exported by Veeam Kasten policies, must meet the system requirements specified in the [Backup Repository Server](https://helpcenter.veeam.com/docs/backup/vsphere/system_requirements.html?ver=120#backup-repository-server) section in the Veeam Backup & Replication User Guide.

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
