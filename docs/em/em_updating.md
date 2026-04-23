---
title: "Updating Enterprise Manager"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_updating.html"
last_updated: "4/22/2026"
product_version: "13.0.1.2067"
---

# Updating Enterprise Manager


Apart from version releases of Veeam Backup Enterprise Manager (for example, 13, 13.0.1), Veeam Software provides updates (for example, update 13.0.1 P1 and 13.0.1 P2). Updates include bug fixes, performance enhancements, and new features.

This article describes how to install updates for Enterprise Manager on Windows. Updated for Enterprise Manager on Linux can be installed automatically. For details, see [Veeam Software Appliance Update](em_update_linux.md).

Before You Begin

Before you install an update for Enterprise Manager 13, check the following prerequisites:

* Make sure you have Enterprise Manager 13.0.1 (build 13.0.1.x.x) of any earlier patch installed.

For information on how to upgrade from version 12.3.1 or later, see [Upgrading to Enterprise Manager 13.0.1](em_upgrading.md).

* With Enterprise Manager and connected backup servers, start the update process with Veeam Backup Enterprise Manager. Backup servers should be updated after that. If you have Veeam Backup & Replication and Veeam Backup Enterprise Manager installed on the same machine, the update wizard will update both products at once.

For more information on the backup server update procedure and prerequisites, see the [Updating Veeam Backup & Replication on Windows](https://helpcenter.veeam.com/docs/vbr/userguide/update_vbr_windows.html?ver=13) section of the Veeam Backup & Replication User Guide.

Performing Update

To install the latest update for Enterprise Manager, perform the following steps:

1. Review [this Veeam KB article](https://www.veeam.com/kb2680) to check if a cumulative patch is available for the version of Veeam Backup Enterprise Manager that is installed.
2. If a cumulative patch is available, click the Veeam KB article link for that cumulative patch.
3. In the Download Information section of the Veeam KB article, click DOWNLOAD PATCH.
4. To launch the update wizard, unzip the downloaded archive and run the Setup.exe file.
5. To install the update, follow the prompts in the update wizard.


