---
title: "cc_object_storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_object_storage.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can allocate object storage resources as cloud repository resources to tenants. To do this, the SP must add an object storage repository in the Veeam Backup & Replication infrastructure and assign this backup repository as a cloud repository in the properties of a tenant account. Once the tenant connects to the SP, they can create backup jobs targeted at the cloud repository that uses object storage as a back end.

This functionality allows the SP to use object storage as a target location for tenant backups without the need to configure scale-out backup repositories extended with capacity tier object storage. It may be helpful, for example, if the SP wants to keep the entire tenant data in object storage instead of offloading backup chains from on-premises extents of a scale-out backup repository to a cloud-based object storage.

The SP can use the following types of object storage as a cloud repository:

* S3 compatible
* Amazon S3, Amazon S3 Glacier and AWS Snowball Edge
* Google Cloud
* IBM Cloud
* Microsoft Azure Blob, Azure Archive Storage and Azure Data Box
* Wasabi Cloud Storage
* Veeam Data Cloud Vault

The SP can add use object storage as a simple backup repository or as an extent of a scale-out backup repository — both as a performance tier extent or capacity tier extent.

Veeam products on the tenant side communicate with the object storage using one of the following connection modes:

* Connection through a gateway server. In this mode, the tenant accesses object storage through a proxy component — a gateway server assigned in the SP Veeam Backup & Replication console. Backup data is sent from Veeam Backup & Replication or Veeam Agent on the tenant side to the gateway server on the SP side, and then it is sent from the gateway server to the object storage used as a cloud repository.
* Direct connection. In this mode, the tenant accesses object storage directly. Backup data is sent from Veeam Backup & Replication or Veeam Agent on the tenant side to the object storage on the SP side.

To access object storage repository in the direct connection mode, Veeam products on the tenant side use temporary credentials issued by Veeam Backup & Replication running on the SP side.

To learn more about connection modes, see [How Backup to Object Storage Works](cc_object_storage_types.md).

Getting Started with Backup to Object Storage

To assign a quota in object storage to the tenant, the SP must complete the following steps:

1. Add an object storage repository in the SP Veeam backup infrastructure. For details, see the [Adding Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/new_object_storage.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. [For S3 compatible object storage] Set up access permissions for the added S3 compatible object storage repository. For details, see the [Managing Permissions for S3 Compatible Object Storage](https://helpcenter.veeam.com/docs/vbr/userguide/access_permissions.html?ver=13#managing-permissions-for-s3-compatible-object-storage) section in the Veeam Backup & Replication User Guide.
2. Assign the added object storage repository as a cloud repository to the tenant account. For details, see [Creating Tenant Accounts](cloud_connect_tenant.md).

Once the tenant connects to the SP, they can create VM backup jobs and Veeam Agent backup jobs targeted at the cloud repository that uses object storage as a back end.

Considerations and Limitations

Backup to object storage in the Veeam Cloud Connect Backup scenario has the following requirements and limitations.

* To be able to back up data to object storage, the tenant must run one of the following Veeam products:

* Veeam Backup & Replication 12 (or later)

For Veeam Data Cloud Vault, both the SP and tenant must run Veeam Backup & Replication 12.1.2 (or later).

* Veeam Agent for Microsoft Windows 6.0 (or later)
* Veeam Agent for Linux 6.0 (or later)
* Veeam Agent for Mac 2.0 (or later)

In earlier product versions, object storage repositories used as cloud repositories are not displayed on the tenant side.

* The Insider Protection functionality is not available to tenant accounts that have at least one object storage repository assigned as a cloud repository.
* Although in the direct connection mode tenant backup data is sent from the tenant side to the object storage on the SP side directly, connection from the tenant Veeam backup server to a cloud gateway is required.
* Object storage repositories used as a cloud repository are not supported by transaction log backup copy jobs.
* The tenant can enable configuration backup in Veeam Backup & Replication and target it at object storage repository used as a cloud repository. In this case, the configuration backup data will be transferred to the object storage through a gateway server regardless of the connection mode specified by the SP in the object storage repository settings.
* Helper appliance used to perform health check for backups that reside in object storage is not supported in Veeam Cloud Connect. If the tenant enables health check in the properties of a backup job targeted at an object storage repository used as a cloud repository, Veeam Backup & Replication will display a message notifying that this operation may require additional costs.
* Data transfer through WAN accelerators is supported only for S3 Compatible object storage repositories in the Connection through a gateway server mode.
* Azure Immutability is not supported for object storage repositories in the Direct connection mode used as cloud repositories.
* For the Google Cloud storage used as a cloud repository, consider the following:

* The Connection through a gateway server mode is supported without prerequisites and limitations.

* To use Google Cloud storage as a cloud repository in the Direct connection mode, you must configure the helper appliance when adding the object storage repository in Veeam Backup & Replication. Although the helper appliance [is not supported](#helper) for health check with object storage repositories, it is required for issuing temporary credentials to enable direct to access the object storage.

* Veeam Data Cloud Vault can only be used as a cloud repository in the Connection through a gateway server mode.
* You cannot use S3 compatible repositories with multiple buckets as a cloud repository.

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
