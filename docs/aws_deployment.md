---
title: "Deployment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_deployment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deployment


To deploy solution architecture components, do the following:

1. Deploy the backup server as described in sections [Installing Veeam Backup & Replication](https://helpcenter.veeam.com/docs/backup/vsphere/install_vbr.html?ver=120) and [Veeam Software Appliance Installation](deployment_linux.md).

Alternatively, you can use a backup server that already exists in your backup infrastructure if it meets the Veeam Plug-in for AWS [system requirements](aws_system_requirements.md).

1. [Install Veeam Plug-in for AWS on the backup server](aws_installing_plugin.md).

This step applies only to Veeam Backup & Replication versions prior to 12. Version 12 (and later) comes with Veeam Plug-in for AWS pre-installed by default.

1. [Deploy a backup appliance in AWS](aws_deploying_appliances.md).

Keep in mind that deployment of backup appliances is supported only in AWS Global, AWS China and AWS GovCloud (US) Regions.

|  |
| --- |
| Important |
| If you install the backup server as described in section Veeam Software Appliance Installation, you will not be able to access the Veeam Plug-in for AWS functionality from the Veeam Backup & Replication Web UI. To work around the issue, [install a remote Veeam Backup & Replication console](install_console.md) — and then log in to the console using the name or IP address of the backup server. For more information, see [Logging in to Veeam Backup & Replication](logon_to_console.md). |

Related Topics

[Appendix E. Uninstalling Backup Appliances Deployed from AWS Marketplace](aws_uninstall.md)

Page updated 2026-06-30

