---
title: "Deployment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_deploying_vb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deployment


To deploy solution architecture components, do the following:

1. Deploy the backup server as described in [Installing Veeam Backup & Replication](install_vbr.md) and [Veeam Software Appliance Installation](deployment_linux.md).

Alternatively, you can use a backup server that already exists in your backup infrastructure if it meets the Veeam Plug-in for Microsoft Azure [system requirements](azure_system_requirements.md).

1. [Install Veeam Plug-in for Microsoft Azure on the backup server](azure_deploying_plug_in.md).

This step applies only to Veeam Backup & Replication versions prior to 12. Version 12 (and later) comes with Veeam Plug-in for Microsoft Azure pre-installed by default.

1. [Deploy a backup appliance in Microsoft Azure](azure_deploying_appliance.md).

|  |
| --- |
| Important |
| If you install the backup server as described in section Veeam Software Appliance Installation, you will not be able to access the Veeam Plug-in for Microsoft Azure functionality from theVeeam Backup & Replication Web UI. To work around the issue, [install a remote Veeam Backup & Replication console](install_console.md) — and then log in to the console using the name or IP address of the backup server. For more information, see [Logging in to Veeam Backup & Replication](logon_to_console.md). |

Related Topics

* [Failure and Recovery](azure_failure_recovery.md)
* [Uninstalling Backup Appliances Deployed from Microsoft Azure Marketplace](azure_uninstalling_vb.md)

Page updated 2026-07-01

