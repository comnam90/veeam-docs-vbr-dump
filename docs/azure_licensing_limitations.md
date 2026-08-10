---
title: "Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_licensing_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Limitations


Keep in mind the following limitations and considerations:

* If you use the Veeam Cloud Connect service provider license, the Veeam Plug-in for Microsoft Azure functionality is available from Veeam Service Provider Console only. For more information, see the Veeam Service Provider Console [Guide for Service Providers](https://helpcenter.veeam.com/docs/vac/provider_admin/integration_clouds.html).

* If you use a Perpetual per-socket license installed on the backup server, and you want to connect a backup appliance to the backup infrastructure, you must install an additional Perpetual per-instance license or a subscription license. When you install an additional license, the new license is automatically merged with the existing Perpetual per-socket license. For more information on the merging process, see [Merging Licenses](license_merge.md).

If you do not install an additional Perpetual per-instance license or a subscription license, you will be able to use one free license instance per each socket (maximum 6 free instances per instance). After you exceed the limit of free instances, backup policies protecting resources that are not covered by the license will fail.

To obtain an additional license, contact a Veeam sales representative at [Sales Inquiry](https://www.veeam.com/salesinc.html).

* If an instance has not been backed up within the past 31 days, Veeam Plug-in for Microsoft Azure automatically revokes the license unit from the instance. If you need to manually revoke a license unit, follow the instructions provided in section [Revoking License Units](azure_license_revoke.md).

Page updated 2026-07-01

