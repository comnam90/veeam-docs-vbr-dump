---
title: "Uninstalling Plug-In"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_uninstalling_plug_in.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Uninstalling Plug-In


Before you uninstall Veeam Plug-in for Microsoft Azure, it is recommended that you [remove all connected backup appliances](azure_removing_appliance_console.md) from the backup infrastructure. If you keep the appliances in the backup infrastructure, the following will happen:

* You will be able to see information on snapshots of Azure VMs and file shares in the Veeam Backup & Replication console. However, you will not be able to perform any operations with these snapshots.

* You will be able to see information on backups of Azure SQL databases. However, you will not be able to perform any operations with these backups.
* You will be able to see information on image-level backups of Azure VMs and perform data recovery operations using these backups. However, restore of entire VMs to Microsoft Azure will start working as described in [How Restore to Microsoft Azure Works](restore_azure_hiw.md).

* You will be able to see information on backup policies. However, you will only be able to remove these policies from the Veeam Backup & Replication console.

To uninstall Veeam Plug-in for Microsoft Azure, do the following:

1. Log in to the backup server using an account with the local Administrator permissions.
2. Open the Start menu, navigate to Control Panel > Programs > Programs and Features.
3. In the program list, click Veeam Plug-in for Microsoft Azure and click Uninstall.
4. In the opened window, click Remove.

![Uninstalling Plug-In](images/azure_uninstall.webp)

|  |
| --- |
| Note |
| After you uninstall Veeam Plug-in for Microsoft Azure, you will be no longer able to add backup appliances and new external repositories to the backup infrastructure. |

Page updated 2026-06-26

