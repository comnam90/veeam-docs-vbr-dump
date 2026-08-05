---
title: "Getting Technical Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_logs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Getting Technical Support


If you have any questions or issues with Veeam Plug-in for AWS, you can search for a resolution on [Veeam R&D Forums](https://forums.veeam.com/) or submit a support case in the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, it is recommended that you provide the Veeam Customer Support Team with the following information:

* [Version information for the product and its infrastructure components](#about)
* The error message or an accurate description of the problem you are facing
* [Log files](#logs)

For information on Veeam Technical Support Tiers, SLAs and coverage, see the [Veeam Customer Support Policy](https://www.veeam.com/support-policy.html).

Viewing Product Details Using Web UI

To view the product details:

1. Switch to the Configuration page.
2. Navigate to Support Information.

The About section of the Updates tab displays the following information:

* Product version — the currently installed version of the backup appliance.
* FLR service version — the currently installed version of the File-level recovery service.
* AWS ID — the unique identification number of the AWS account where the backup appliance is installed.
* Support ID — the unique identification number of the Veeam support contract.

[![Viewing Product Details](images/aws_support_details.webp)](images/aws_support_details.webp "Viewing Product Details")

Downloading Product Logs Using Web UI

To download the product logs, do the following:

1. Switch to the Download Logs tab.
2. Click Download Logs.
3. In the Download Logs window, specify a time interval for which logs must be collected:

* Select the Collect logs for the last option if you want to collect data for a specific number of days in the past.

* Select the Collect logs for specified time period option if you want to collect data for a specific period of time in the past.

1. Click OK.

The backup appliance will collect logs for the specified time interval and save them to the default download folder on the local machine in a single log.zip archive.

[![Collecting Logs](images/aws_support_logs.webp)](images/aws_support_logs.webp "Collecting Logs")

Downloading Product Logs Using Veeam Backup & Replication Console

To export the product logs, do the following:

1. In the Veeam Backup & Replication console, open the main menu and navigate to Help > Support Information.
2. In the Export Logs wizard, do the following:

1. At the Scope step, select the Export all logs for selected components option. Then, in the Managed servers list, select the backup server, backup appliances and other components for which you want to export logs.
2. Complete the wizard as described in section [Export Logs](export_logs_date.md).

![Getting Technical Support](images/aws_export_logs.webp)

Page updated 2026-05-21

