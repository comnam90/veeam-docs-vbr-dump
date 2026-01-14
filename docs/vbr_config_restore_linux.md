---
title: "Restoring Configuration Database on Linux-Based Backup Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_restore_linux.html"
last_updated: "11/24/2025"
product_version: "13.0.1.1071"
---

# Restoring Configuration Database on Linux-Based Backup Server

In this article

Restore of the configuration database is helpful in the following situations:

* The configuration database got corrupted and you want to quickly recover data from the configuration backup.
* You want to roll back the configuration database to a specific point in time.

You can start a configuration restore in one of the following ways:

* [Using an answer file](vbr_config_restore_unattended_linux.md) on the backup server side under the root account.
* [Using Veeam Host Management](vbr_config_restore_hmc.md).

|  |
| --- |
| Important |
| We strongly recommend using only the configuration database restore process to migrate Veeam Backup & Replication configuration database to another backup server. |

Page updated 11/24/2025

Page content applies to build 13.0.1.1071
