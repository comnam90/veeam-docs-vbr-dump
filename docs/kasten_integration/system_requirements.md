---
title: "System Requirements"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/system_requirements.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements


Before you start using Veeam Plug-in for Kasten, consider the following:

Backup Server

The machine where the Veeam Plug-in for Kasten will run must meet the system requirements described in the [System Requirements](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13) section in the Veeam Backup & Replication User Guide.

Additionally, the following software must be installed:

* Microsoft .NET Core Runtime 10.0
* Microsoft ASP.NET Core Shared Framework 10.0

|  |
| --- |
| Important |
| Microsoft ASP.NET Core Shared Framework and Microsoft .NET Core Runtime must be of the same version (up to the minor version number).  For example, if the version of Microsoft ASP.NET Core Shared Framework is 10.0.7, then the version of Microsoft .NET Core Runtime must also be 10.0.7. |

Starting from version 6.5.9, Veeam Plug-in for Kasten no longer supports Veeam Backup & Replication installed on Microsoft Windows Server 2012 and 2012 R2.

Kubernetes Distribution Requirements

Veeam Plug-in for Kasten supports only backup exports of Kubernetes persistent volumes to Veeam backup repositories. For details on which volumes are supported for export to a VBR repository, see [Veeam Kasten Docs](https://docs.kasten.io/latest/install/storage/#vbr-integration).

Kasten Application Version

A Veeam Kasten application must be the 5.5.3 version or higher.

Kasten Dashboard Access

An external access to the Kasten dashboard must be set up. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/access/dashboard.html).

Veeam Backup & Replication

Veeam Plug-in for Kasten version 13.2.1.60 supports integration with Veeam Backup & Replication version 13.1.

Veeam Backup Repositories Requirements

Veeam backup repositories, where you want to keep backups exported by Veeam Kasten policies, must meet the system requirements specified in the [Backup Repository Server](https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html?ver=13) section in the Veeam Backup & Replication User Guide.

Page updated 2026-08-04

