---
title: "Removing License"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_license_remove.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Removing License


To remove the license installed on a backup appliance that was previously deployed from the Microsoft Azure Marketplace:

1. Switch to the Configuration page.
2. Navigate to Licensing > License Info.
3. Click Remove License.
4. In the Remove License window, click Yes to confirm that you want to remove the license.

[![Removing License](images/azure_removing_license.webp)](images/azure_removing_license.webp "Removing License")

After you remove a license, Veeam Backup for Microsoft Azure will automatically switch back to the Free edition. In this case, according to the FIFO (first-in first-out) queue, only the first 10 instances registered in the configuration database will remain protected. You can revoke license units from these instances as described in section [Revoking License Units](azure_license_revoke.md).

|  |
| --- |
| Note |
| If you remove a license installed on a backup appliance that is not managed by any Veeam Backup & Replication server, you will no longer be able to install a license on that backup appliance again — unless you [install Veeam Plug-in for Microsoft Azure on a backup server](azure_deploying_plug_in.md) and [add the appliance](azure_adding_appliance_console.md) to the backup infrastructure. |

Related Topics

[Viewing License Information](azure_license_view_information.md)

Page updated 2025-06-03

