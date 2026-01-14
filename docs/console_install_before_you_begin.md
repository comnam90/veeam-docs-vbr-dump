---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/console_install_before_you_begin.html"
last_updated: "7/21/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you install the Veeam Backup & Replication console, consider the following:

* The Veeam Backup & Replication console must be of the same version as Veeam Backup & Replication installed on the backup server.
* A machine on which you plan to install the Veeam Backup & Replication console must meet the system requirements. For more information, see [System Requirements](system_requirements.md#console).
* A user account that you plan to use for installation must have sufficient permissions. For more information, see [Permissions](required_permissions.md).
* Backup infrastructure components communicate with each other over specific ports. These ports must be open. For more information, see [Ports](used_ports.md).
* We do not recommend installing the Veeam Backup & Replication console on the machine that is used in the role of a different backup infrastructure component, for example, as a backup repository. Different components have different services installed on the server. Upon upgrading the console to the new version, your backup infrastructure may get out-of-order.

Page updated 7/21/2025

Page content applies to build 13.0.1.1071
