---
title: "Getting Technical Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_export_logs.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Getting Technical Support


If you have any questions or issues with Veeam Plug-in for HPE Morpheus VM Essentials, you can search for a resolution on [Veeam R&D Forums](https://forums.veeam.com/) or submit a support case in the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, it is recommended that you provide the Veeam Customer Support Team with the following information:

* [Version information for the product and its infrastructure components](#ViewingProductDetails)
* The error message or an accurate description of the problem you are facing
* [Log files](#DownloadingLogs)

Viewing Product Details

To view the product details in a Windows-based environment, do the following:

1. On the server running the Veeam Backup & Replication console, navigate to Settings> Apps & features.

Alternatively, open the Control Panel window and navigate to Programs > Programs and Features.

1. In the program list, check the version of Veeam Plug-in for HPE Morpheus VM Essentials.

[![Viewing Product Details](images/hpe_plugin_version.webp)](images/hpe_plugin_version.webp "Viewing Product Details")

|  |
| --- |
| Tip |
| To view the product details in a Linux-based environment, follow the instructions provided in section [Performing Maintenance Tasks](hmc_perform_maintenance_tasks.md#managing-veeam-components).. |

To view the product details, do the following:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Managed Servers.
3. In the working area, select the HPE Morpheus VM Essentials manager and click Edit Server on the ribbon, or right-click the HPE Morpheus VM Essentials manager and select Properties.
4. In the Edit HPE Morpheus VM Essentials Server wizard, click Finish.
5. Wait for Veeam Plug-in for HPE Morpheus VM Essentials to complete the configuration check and click Next.

At the Summary step of the wizard, the following information will be displayed:

* HPE Morpheus VM Essentials manager hostname or IP address
* Current version of HPE Morpheus VM Essentials
* Account that is used to connect to the HPE Morpheus VM Essentials manager

![Getting Technical Support](images/hpe_server_edit_version.webp)

Downloading Logs

To download the product logs in a Windows-based environment, do the following:

1. From the main menu of the Veeam Backup & Replication console, select Help > Support Information.
2. At the Scope step of the Export Logs wizard, select the Export all logs for selected components option. Then, in the Managed servers list, select the backup server.

Complete the wizard as described in section [Exporting Logs](exporting_logs.md).

[![Exporting Logs Using Veeam Backup & Replication Console](images/hpe_logs_vbr.webp)](images/hpe_logs_vbr.webp "Exporting Logs Using Veeam Backup & Replication Console")

|  |
| --- |
| Tip |
| To download the product logs in a Linux-based environment, follow the instructions provided in section [Performing Maintenance Tasks](hmc_perform_maintenance_tasks.md#downloading-logs). |


