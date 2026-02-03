---
title: "Getting Technical Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_export_logs.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# Getting Technical Support


If you have any questions or issues with Veeam Plug-in for Proxmox VE, you can search for a resolution on [Veeam R&D Forums](https://forums.veeam.com/) or submit a support case in the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, it is recommended that you provide the Veeam Customer Support Team with the following information:

* [Version information for the product and its infrastructure components](#ViewingProductDetails)
* The error message or an accurate description of the problem you are facing
* [Log files](#DownloadingLogs)

Viewing Product Details

To view the product details, do the following:

1. On the server running the Veeam Backup & Replication console, navigate to Settings> Apps & features.

Alternatively, open the Control Panel window and navigate to Programs > Programs and Features.

1. In the program list, check the version of Veeam Plug-In for Proxmox Virtual Environment.

[![Viewing Product Details](images/pve_plugin_version.webp)](images/pve_plugin_version.webp "Viewing Product Details")

Downloading Logs

To download the product logs, do the following:

1. From the main menu of the Veeam Backup & Replication console, select Help > Support Information.
2. At the Scope step of the Export Logs wizard, select the Export all logs for selected components option. Then, in the Managed servers list, select the backup server.

Complete the wizard as described in section [Exporting Logs](exporting_logs.md).

[![Exporting Logs Using Veeam Backup & Replication Console](images/pve_logs_vbr.webp)](images/pve_logs_vbr.webp "Exporting Logs Using Veeam Backup & Replication Console")


