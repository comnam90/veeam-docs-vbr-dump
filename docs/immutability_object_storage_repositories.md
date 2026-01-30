---
title: "Immutability for Object Storage Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_object_storage_repositories.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# Immutability for Object Storage Repositories


Veeam Backup & Replication allows you to prohibit deletion of data from the object storage repository by making that data temporarily immutable and to protect data against malware activity by maintaining several versions of a single backup.

The immutability feature can help in the following cases:

* Data on the object storage is corrupted.
* Retention policy is set to keep only one restore point.
* Due to the hacker attack, the retention policy has been modified to a shorter period. For example, instead of keeping data for 5 days, the retention is set to keep it for only 1 day.

After you enable immutability, you will not be able to perform the following operations with the immutable data stored on object storage repositories:

* Manual data removal, as described in section [Deleting Backups from Scale-Out Backup Repositories](deleting_backups_from_sobr.md).
* Removal of data by the retention policy, as described in section [Retention Policy](capacity_tier_retention.md).
* Removal of data using any cloud service provider tools, for example an S3 browser.
* Removal of data by the cloud service provider technical support department.

* Removal of data by the Remove deleted items data after option. For more information, see the Maintenance Settings section for [VMware vSphere backup jobs](backup_job_advanced_maintenance_vm.md) and [Microsoft Hyper-V backup jobs](backup_job_advanced_maintenance_hv.md).

You can use immutability for data stored in the following types of object storage repositories:

* Veeam Data Cloud Vault
* Amazon S3
* S3-compatible
* Microsoft Azure Storage
* Google Cloud Storage
* IBM Cloud Object Storage
* Wasabi Cloud Object Storage
* 11:11 Cloud Object Storage

Related Topics

[Considerations and Limitations](os_immutability_limitations.md)

[How Immutability Works](hiw_immutability_os.md)

[Block Generation](object_storage_block_generation.md)

[Enabling Immutability](immutability_os_enable.md)


