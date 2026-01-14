---
title: "Restoring Configuration Database using Answer File"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vbr_config_restore_unattended_linux.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Restoring Configuration Database using Answer File

In this article

Restore of the configuration database is helpful in the following situations:

* The configuration database got corrupted and you want to quickly recover data from the configuration backup.
* You want to roll back the configuration database to a specific point in time.

The configuration database restore is initiated by running the Veeam.Backup.Configuration.UnattendedRestore.dll on the backup server side under the root account. You can restore a configuration backup on the same backup server where the backup was created or on another backup server.

Before you start the restore process, [check prerequisites](restore_vbr_linux_byb.md). Then perform the following steps:

1. [Generate Answer File](restore_vbr_linux_generate.md).
2. [Edit Answer File](restore_vbr_linux_edit.md).
3. [Start Restore Process](restore_vbr_linux_start.md).
4. [Finalize Restore Process](restore_vbr_linux_finalize.md).

Page updated 11/26/2025

Page content applies to build 13.0.1.1071
