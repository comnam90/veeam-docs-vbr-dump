---
title: "managing_licenses"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/managing_licenses.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---


In this article

The Veeam Backup & Replication infrastructure requires a license to process backup and replication jobs. Using Enterprise Manager to manage Veeam Backup & Replication licenses reduces administration overhead. You can manage and activate licenses for the entire backup infrastructure from a single web console. Enterprise Manager allows you to view what workloads consume instances in the license, install a new license, and revoke the license from protected workloads.

Veeam Backup Enterprise Manager collects information about the type of license installed on added backup servers and the number of instances in the license. When Enterprise Manager collects data from backup servers, it also synchronizes license data by checking if the license installed on the backup server matches with the license installed on the Enterprise Manager server. If the licenses do not match, the license on the backup server is automatically updated to match the license of the Enterprise Manager server.

When you run a job, Enterprise Manager uses instances required for each type of protected workloads. If a workload is protected by multiple backup servers added to the Enterprise Manager infrastructure, the workload will consume the Enterprise Manager license only once.

Consider the following:

* Enterprise Manager on Linux is supported only with the Enterprise Plus edition license.
* Socket licenses are supported for Enterprise Manager on Windows only.
* You cannot use the same Enterprise Manager server to manage backup servers that require different licenses, for example, a backup server of a Veeam Cloud Connect service provider and a regular backup server used to process Veeam Backup & Replication jobs. For example, you add to Enterprise Manager a backup server with the Veeam Cloud Connect service provider license installed. Enterprise Manager will obtain information about the license and save it to its database. If you then add another backup server with a different type of license installed, Enterprise Manager will install the Veeam Cloud Connect service provider license on this backup server. As a result, you will be able to use the second backup server to configure the Veeam Cloud Connect infrastructure, and will not be able to use this server to run backup and replication jobs.
* For information on Veeam Backup & Replication license types, see the [Licensing](https://helpcenter.veeam.com/docs/vbr/userguide/licensing.html?ver=13) section of the Veeam Backup & Replication User Guide.
* For information on Veeam Cloud Connect license types and license management tasks, see the [Licensing for Service Providers](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_licensing.html?ver=13) section of the Veeam Cloud Connect Guide.
* For more information on Veeam licensing, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

In This Section

* [Installing License](em_license_install.md)
* [Viewing License Details](viewing_changing_current_license.md)

* [Updating License](em_license_update.md)

* [Revoking License](revoking_licensed_hosts.md)
* [Removing License](removing_license.md)
* [Managing Monthly Usage Reports](em_license_usage_manage.md)

Page updated 11/21/2025

Page content applies to build 13.0.1.1071
