---
title: "cloud_connect_machine_count"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_machine_count.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication offers several ways to view information about protected tenant workloads — machines processed by tenant jobs targeted at cloud repositories and cloud hosts.

* License. The SP can view the number of tenant machines that consume points in the license. To learn more, see [Viewing License Information](sp_view_license.md).
* License usage report. Veeam Backup & Replication displays the number of tenant machines that use points in the license in the license usage report. The SP can view monthly reports generated automatically by Veeam Backup & Replication or generate the report manually when needed. To learn more, see [Managing License Usage Reports](sp_license_usage_manage.md).

The SP can also use Veeam PowerShell and Veeam Backup Enterprise Manager REST API to obtain information about protected tenant workloads.

* Veeam PowerShell displays the total number of tenant machines (excluding rental machines and new workloads) that have been processed by Veeam Backup & Replication in the past 31 days and use points in the license. To learn more, see the [Get-VBRCloudTenant](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenant.html?ver=13) section in the Veeam PowerShell Reference.
* Veeam Backup Enterprise Manager REST API displays the number of machines per tenant that have been processed by Veeam Backup & Replication in the past 31 days and use points in the license. The number of rental machines and the number of new workloads are displayed separately for each tenant. To learn more, see the following sections in the Veeam Backup Enterprise Manager REST API Reference:

* [/cloud/tenants/{ID}](https://helpcenter.veeam.com/docs/backup/em_rest/tenants_id.html?ver=120)
* [GET /cloud/tenants/{ID}/freelicenseCounters](https://helpcenter.veeam.com/docs/backup/em_rest/get_cloud_tenants_id_freelicensecounters.html?ver=120)

|  |
| --- |
| Note |
| Consider the following:   * If the SP manages the Veeam backup infrastructure using Veeam Service Provider Console, they can view information about protected tenant workloads in Veeam Service Provider Console. For more information, refer to the [Veeam Service Provider Console documentation](https://helpcenter.veeam.com/docs/vac/provider_admin/cc_license.html?ver=9).   For example, if you use Veeam Service Provider Console REST API v3.6, see the [Get All Companies](https://helpcenter.veeam.com/docs/vac/rest/reference/vspc-rest.html?ver=9#tag/Companies/operation/GetCompanies) and [Get License Usage by All Organizations](https://helpcenter.veeam.com/docs/vac/rest/reference/vspc-rest.html?ver=9#tag/Licensing/operation/GetOrganizationsLicenseUsage) sections in the Veeam Service Provider Console REST API Reference.   * The SP can also view the number of tenant machines whose backups and replicas consume resources in the SP Veeam Cloud Connect infrastructure. Veeam Backup & Replication displays this information in the Tenants node of the Cloud Connect view in the SP backup console. To learn more, see [Viewing Tenant Account Information](cloud_connect_view.md). |

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
