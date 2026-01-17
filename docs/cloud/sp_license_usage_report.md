---
title: "License Usage Reporting"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/sp_license_usage_report.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# License Usage Reporting


The SP must periodically submit a license usage report. There are different mechanisms to do so. If the SP uses Veeam Service Provider Console to manage the Veeam backup infrastructure, they collect license usage reports in Veeam Service Provider Console and submit reports using the VCSP Pulse portal (or an aggregator reporting portal).

For more information on how Rental licensing works for various workloads within Veeam Platform, how to manage licenses using Veeam Service Provider Console and VCSP Pulse, and how to collect and report the license usage, see the [Veeam Rental Licensing and Usage Reporting Guide](https://helpcenter.veeam.com/docs/vcsp/refguide/about.html).

Veeam Backup & Replication also allows the SP to submit license usage reports from the Veeam backup console. This section provides a detailed description of reporting mechanisms offered by Veeam Backup & Replication.

The SP submits a license usage report monthly, starting from the first day of the month.

* For the Veeam Cloud Connect license, the SP reports the number of used points (excluding points used by [new workloads](cloud_connect_sp_license.md#new_vms)). The report also contains the license information and the number of machines backed up and replicated per tenant. The report serves as a basis for issuing invoices for the Veeam Cloud Connect rental program.

The report does not include rental machines. To learn more, see [Rental Machines Licensing](cloud_connect_rental_lic.md).

* For the Rental Veeam Backup & Replication license, the SP reports the number of used points (excluding points used by [new workloads](cloud_connect_hosting_licenses.md#new_vms)). The report also contains the license information, the number of processed machines (VMs, workstations and servers) and information about machines and jobs that process these machines.

Veeam Backup & Replication offers two methods of license usage reporting:

* Automatic reporting — the recommended usage reporting method. The method is used when license auto update is enabled. To learn more, see [Automatic License Usage Reporting](sp_license_usage_report_online.md).
* Manual reporting — the usage reporting method intended for Veeam backup servers that do not have permanent connection to the internet. Manual reporting is used when license auto update is disabled. To learn more, see [Manual License Usage Reporting](sp_license_usage_report_offline.md).

The SP can review and adjust the usage report before submitting it to Veeam. To learn more, see [Managing License Usage Reports](sp_license_usage_manage.md).

|  |
| --- |
| Note |
| If the same Rental Veeam Backup & Replication license is installed on multiple tenant backup servers and the SP does not use the Veeam Service Provider Console to manage the Veeam backup infrastructure, the SP must report license usage for all Veeam Backup & Replication servers in one of the following ways:   * The SP must send individual license usage reports from each backup server separately using the Veeam Backup & Replication console. * For tenant backup servers that are connected to the Veeam Backup Enterprise Manager, a single report containing license usage information from each backup server is generated on the Veeam Backup Enterprise Manager server. In this case, the SP must send information about the license usage information from the Veeam Backup Enterprise Manager. * Auto-Populate and Auto-Submit (APAS) reports can be used. To do that, the SP must properly manage license keys and review the report before it is submitted. To learn more, see the [Auto-Populate and Auto-Submit Usage Reporting](https://helpcenter.veeam.com/docs/vcsp/refguide/apas.html) section in the Veeam Rental Licensing and Usage Reporting Guide. |


