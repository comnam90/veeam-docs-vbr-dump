---
title: "getting_started"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/getting_started.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Explorers is a set of applications that allows you to manage application items from the following sources:

* Backups and replicas created with Veeam Backup & Replication
* Backups created with Veeam Backup for Microsoft 365

Every set of Veeam Explorer applications comes with its own PowerShell extension. Each extension includes a Microsoft Windows PowerShell module that provides a set of PowerShell cmdlets and allows you to perform the following operations:

* Restore application items
* Export application items
* Publish and unpublish databases

The following table lists all Veeam Explorers PowerShell modules that come as part of Veeam Backup & Replication and Veeam Backup for Microsoft 365.

| Module | Veeam Explorer | Veeam Backup & Replication | Veeam Backup for Microsoft 365 |
| --- | --- | --- | --- |
| Veeam.Exchange.PowerShell | Veeam Explorer for Microsoft Exchange | ✔ | ✔ |
| Veeam.SharePoint.PowerShell | Veeam Explorer for Microsoft SharePoint and Veeam Explorer for Microsoft OneDrive for Business | ✔ | ✔ |
| Veeam.Teams.PowerShell | Veeam Explorer for Microsoft Teams | ✔ | ✔ |
| Veeam.ActiveDirectory.PowerShell | Veeam Explorer for Microsoft Active Directory | ✔ | ✖ |
| Veeam.SQL.PowerShell | Veeam Explorer for Microsoft SQL Server | ✔ | ✖ |
| Veeam.Oracle.PowerShell | Veeam Explorer for Oracle | ✔ | ✖ |
| Veeam.PostgreSQL.PowerShell | Veeam Explorer for PostgreSQL | ✔ | ✖ |
| Veeam.SapHana.PowerShell | Veeam Explorer for SAP HANA | ✔ | ✖ |
| Veeam.MongoDB.PowerShell | Veeam Explorer for MongoDB | ✔ | ✖ |

To see a version of this document that only contains information on the modules that come with Veeam Backup for Microsoft 365 installations, see [Veeam Explorers PowerShell Reference](https://helpcenter.veeam.com/docs/vbo365/explorers_powershell/getting_started.html?ver=80).

Requirements

The machine that runs the PowerShell session must have PowerShell version 7 or later installed.

Consider the following:

* If you are running the PowerShell session on a Windows machine that is not a Veeam Backup & Replication backup server, you must install the Veeam Backup & Replication console. For more information on how to install Veeam Backup & Replication console, see the [Installing Veeam Backup & Replication Console](https://helpcenter.veeam.com/docs/vbr/userguide/install_console.html?ver=13) section of the Veeam Backup & Replication User Guide.
* If you are running the PowerShell session on a machine that is not a Veeam Backup for Microsoft 365 server, you must install the Veeam Backup for Microsoft 365 PowerShell toolkit. For more information on how to install the PowerShell toolkit, see the [Installing PowerShell Toolkit](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_installing_ps.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide.
* To use Veeam Explorer PowerShell cmdlets that come with Veeam Backup & Replication  installations, you must have the Veeam Backup Administrator role. For more information, see the [Configuring Roles](https://helpcenter.veeam.com/docs/vbr/userguide/configure_roles.html?ver=13) section of the Veeam Backup & Replication User Guide.

* If you are restoring data from backups or replicas created by Veeam Backup & Replication  and you are running the PowerShell session on a Linux machine, you can only use the Veeam.Oracle.PowerShell, Veeam.PostgreSQL.PowerShell, Veeam.MongoDB.PowerShell and Veeam.SapHana.PowerShell modules.
* If you are restoring data from backups created by Veeam Backup for Microsoft 365, the Veeam Explorers version must be the same as the Veeam Backup for Microsoft 365 version. For example, to export Exchange items from backups created by Veeam Backup for Microsoft 365 version 8, Veeam Explorer for Microsoft Exchange version 8 must be installed on your machine.

In This Section

* [Starting PowerShell Sessions](ps_sessions.md)
* [Understanding Veeam Explorers Cmdlets](understanding_veeam_explorers_cmdlets.md)
* [Using Get-Help](using_get-help.md)
* [Examples of Use](examples_of_use.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
