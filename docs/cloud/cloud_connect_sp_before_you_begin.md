---
title: "cloud_connect_sp_before_you_begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_sp_before_you_begin.html"
last_updated: "7/22/2024"
product_version: "13.0.1.1071"
---


In this article

Before you add a SP, complete the following prerequisites:

* Make sure that the SP has provided you with the following information:

* You have a user name and password for your tenant account registered at the SP Veeam backup server.
* You have a full DNS name or IP address of the cloud gateway over which you will communicate with the Veeam Cloud Connect infrastructure.
* You have a port over which to connect to the cloud gateway (if the SP specified a non-default port).
* [Optional] You have a TLS certificate thumbprint that you can use for TLS certificates verification.

* [For standalone tenant accounts] It is recommended that you change the password for the root account of the tenant-side network extension appliance before connecting to the SP. You can change the password in the service credentials record using the Credentials Manager. This operation is performed in the similar way as on the SP side. To learn more, see [Managing Credentials](cloud_connect_tenant_appliance_credentials.md).
* The tenant can add the SP on more than one backup server using the same tenant account credentials. This may be useful, for example, if the tenant wants to restore data from a cloud backup after the original tenant backup server becomes unavailable. In this scenario, backups created by the tenant on any of the backup servers connected to the SP become available on each backup server.

For this scenario, consider the following:

* All backup servers where the tenant plans to add the SP must run the same Veeam Backup & Replication version.
* When you delete a cloud backup in Veeam Backup & Replication, the backup is removed from the cloud repository and becomes unavailable on all backup servers connected to the SP. To learn more, see [Deleting from Disk](delete_backup_from_disk.md).
* Keep in mind that adding the same SP on multiple backup servers and creating backups under the same tenant account may complicate management of cloud backups in Veeam Backup & Replication.

Page updated 7/22/2024

Page content applies to build 13.0.1.1071
