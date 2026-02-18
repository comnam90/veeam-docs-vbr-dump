---
title: "Microsoft Azure Object Storage Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_limitations.html"
last_updated: "2/17/2026"
product_version: "13.0.1.1071"
---

# Microsoft Azure Object Storage Considerations and Limitations


General Considerations and Limitations

Consider the following limitations:

* Data in an Azure container must be managed solely by Veeam Backup & Replication, including retention and data management. When you enable version-level immutability for the Azure container, make sure that you do NOT enable the default retention option. Note that enabling lifecycle rules is not supported and may result in backup and restore failures.
* [For Microsoft Azure Blob storage] Veeam Backup & Replication does not support soft delete for blobs.
* [For Microsoft Azure Archive storage] Microsoft Azure has certain limits (quotas) on maximum amount of resources used. The quotas depend on the type of proxies you have selected. If you exhaust a quota, you will be unable to use Microsoft Azure Archive storage. For more information about Microsoft Azure quotas, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits).
* Veeam Backup & Replication performs operations only on a blob level. You cannot create Azure containers or storage accounts from the backup infrastructure.
* Veeam Backup & Replication does not support object-level immutability and default immutability policies assigned to Azure storage accounts. You must set immutability for an Azure container where backed-up objects will reside. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal#create-a-storage-account-1).
* Veeam Backup & Replication supports all types of Azure Storage redundancy. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy).

|  |
| --- |
| Note |
| Note that the support of storage redundancy depends on the type of the Microsoft Azure Storage. For example. Microsoft Azure Archive Storage with the archive access tier does not support Azure accounts with the following redundancy options: zone-redundant storage (ZRS), geo-redundant storage (GZRS) and read-access geo-zone-redundant storage (RA-GZRS). For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview#archive-access-tier). |

Azure Storage Access Tier Considerations

Consider the following access tier limitations:

* For [Azure Blob Storage](osr_adding_blob_storage.md), Veeam Backup & Replication supports hot and cool access tiers.

|  |
| --- |
| Important |
| If your Azure storage account access tier differs from the access tier specified for Azure object storage in Veeam Backup & Replication, Azure applies storage class as follows:   * If you specify the hot access tier at the [Container step](azure_storage_details.md#accesstier) of the New Object Storage wizard, but the Azure storage account is set to either cool or cold access tier, Azure Blob Storage applies the inferred access tier to both data and metadata. For example, if you set the Azure object storage to hot access tier, but the Azure storage account is set to cool, Azure will apply the cool tier for both backup data and metadata. * If you specify the cool access tier at the [Container step](azure_storage_details.md#accesstier) of the New Object Storage wizard, but the Azure storage account is set to either hot or cold access tier, Azure Blob Storage applies the cool access tier for backup data and the inferred access tier for metadata. For example, if you set the Azure object storage to cool access tier, but the Azure storage account  is set to hot access tier, Azure Blob will apply cool access tier for backup data and hot access tier for metadata. |

* For [Azure Archive Storage](osr_adding_blob_storage_archive_tier.md), Veeam Backup & Replication supports cold and archive access tiers.

Immutability Limitations

Consider the following [immutability](immutability_object_storage_repositories.md) limitations for Microsoft Azure Storage:

* Veeam Backup & Replication supports the Versioning feature for Microsoft Azure object storage for which [immutability](immutability_object_storage_repositories.md) is enabled.

* Make sure that the Microsoft Azure Storage settings meet the following requirements when you configure an Azure storage account:

* When you create a storage account, ensure that you enable versioning for blobs.
* When you create a storage account, do NOT enable version-level immutability. By default, this option is enabled and you must disable it. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-support-on-a-storage-account).

* Make sure that the Microsoft Azure Storage settings meet the following requirements when you configure an Azure container:

* When you create a container, you must enable version-level immutability. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-for-a-new-container).
* When you create a container, ensure that the default retention is disabled. For more information on how to disable retention settings for Azure container, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-container-scope?tabs=azure-portal).

|  |
| --- |
| Tip |
| For instruction on how to configure your Azure storage account with the necessary settings, see [this Veeam KB article](https://www.veeam.com/kb4416). |

* The default immutability policies are not supported.
* Do NOT enable immutability for already existing containers in the Azure portal. Otherwise, Veeam Backup & Replication will not be able to process these containers properly and it may result in data loss.

* Version-level immutability for Azure storage accounts is not supported.

* [For backup jobs managed by Veeam Agent] You cannot back up data to Microsoft Azure object storage added in the direct connection mode.

* [For Veeam Cloud Connect] Microsoft Azure object storage cannot be used as a cloud repository in the direct connection mode.


