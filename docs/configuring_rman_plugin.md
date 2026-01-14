---
title: "Configuring Veeam Plug-In for Oracle RMAN"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configuring_rman_plugin.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Configuring Veeam Plug-In for Oracle RMAN

In this article

By default, RMAN sends backups to a native RMAN location on disk (DEFAULT DEVICE TYPE TO DISK). When you configure Veeam Plug-In, the default device type is changed to SBT\_TAPE, which gives control over backup media management to Veeam Plug-In. Thus, after you deploy Veeam Plug-In on an Oracle server, you can perform all backup and restore operations in the Oracle RMAN console. Veeam Plug-In compresses database backups and transfers them to a backup repository connected to Veeam Backup & Replication.

To use Veeam Plug-In you must configure the connection between the Oracle server, Veeam Backup & Replication server and backup repositories where backup files will be stored.

* [Configuring Plug-In on Linux or Unix](configuring_rman_plugin_lin.md)
* [Configuring Plug-In on Microsoft Windows](configuring_rman_plugin_win.md)

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
