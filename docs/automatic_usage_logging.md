---
title: "Automatic License Usage Reporting"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/automatic_usage_logging.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Automatic License Usage Reporting


When license auto update is enabled for [Rental, Subscription, Perpetual](types_of_licenses.md#rental) licenses, Veeam Backup & Replication performs automatic license usage reporting.

As part of reporting, Veeam Backup & Replication collects statistics on the current license usage and sends it periodically to the Veeam License Update Server. The report provides information about the contract ID, product installation ID, and the maximum number of licensed objects that were managed by Veeam Backup & Replication over the past week (high watermark). The reporting process runs in the background mode, once a week at a random time and day.

The type of reported objects is defined by the product and the installed license. The report can include information about VMs, workstations or servers protected with Veeam backup agents, and so on.

The collected data does not include information on the usage of Veeam Backup & Replication by any individual person identifiable for Veeam, or any data protected by Veeam Backup & Replication.

The collected data allows our back-end system to automatically approve your monthly usage reports as long as they do not deviate from the high watermark value significantly. This helps to keep our report processing costs low, thus allowing us to maintain low rental prices for our solution. Veeam may also use collected data for any other internal business purposes it deems appropriate, including (but not limited to) evaluation, improvement and optimization of Veeam licensing models.

By enabling license auto update you agree with collection, transmission and use of the reporting data. You must not enable license auto update in case you do not agree with such collection, transmission and use.


