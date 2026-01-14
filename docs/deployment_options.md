---
title: "Deployment Options"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_options.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---

# Deployment Options

In this article

For  Veeam Backup & Replication on Linux, Veeam provides the following deployment options:

| Deployment Option | Description |
| --- | --- |
| Veeam Software Appliance ISO/OVA | Used to configure a Veeam Backup & Replication server or Veeam Backup Enterprise Manager server. This bundle includes customized Rocky Linux distribution and components that Veeam Backup & Replication or Veeam Backup Enterprise Manager requires to work properly.  For more information on installing Veeam Software Appliance from the ISO or OVA file, see the following sections:   * [Veeam Software Appliance Installation](deployment_linux.md) in the Veeam Backup & Replication User Guide. * [Veeam Software Appliance Installation](https://helpcenter.veeam.com/docs/vbr/em/deployment_linux.html?ver=13) in the Enterprise Manager User Guide.   Note: To access a Linux-based Veeam Backup & Replication server remotely, you can only install the Veeam Backup & Replication console on a dedicated Microsoft Windows machine or use the web UI. For more information, see [Veeam Backup & Replication Console Installation](deploy_console.md) and [Veeam Backup & Replication Web UI](vbr_web_console.md). |
| Veeam LiveOS ISO | Used to boot Veeam Software Appliance or Veeam Infrastructure Appliance in a live mode to resolve user authentication issues when standard methods described in the [Managing User Authentication](hmc_manage_user_auth.md) section cannot be applied. For more information, see [this KB article](https://www.veeam.com/kb4761). |
| Veeam Infrastructure Appliance ISO | Used as a recommended alternative for configuring Linux-based backup infrastructure components. This bundle includes customized Rocky Linux distribution and required Veeam components. For the full list of the roles that can be assigned to a Linux server deployed from Veeam Infrastructure Appliance, see [Considerations and Limitations](linux_infrastructure_appliance_byb.md).  For more information on installing Veeam Infrastructure Appliance from the JeOS ISO file, see [Installing Veeam Infrastructure Appliance with ISO](linux_infrastructure_appliance_install.md). |

For  Veeam Backup & Replication on Windows, Veeam provides a Veeam Backup & Replication ISO file to deploy or upgrade the following components:

* Veeam Backup & Replication server. For more information, see [Veeam Backup & Replication Installation on Microsoft Windows](installation.md).
* Veeam Backup & Replication console — can be installed on the Microsoft Windows machine with the Veeam Backup & Replication server or on a dedicated Microsoft Windows machine. For more information, see [Veeam Backup & Replication Console Installation](deploy_console.md).
* Veeam Backup Enterprise Manager server — can be installed on the Microsoft Windows machine with the Veeam Backup & Replication server or on a dedicated Microsoft Windows machine. For more information, see [Enterprise Manager Deployment on Windows](https://helpcenter.veeam.com/docs/backup/em/deployment.html) in the Enterprise Manager User Guide.

Page updated 11/3/2025

Page content applies to build 13.0.1.1071
