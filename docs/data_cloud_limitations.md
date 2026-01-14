---
title: "Veeam Data Cloud Vault Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_cloud_limitations.html"
last_updated: "12/1/2025"
product_version: "13.0.1.1071"
---

# Veeam Data Cloud Vault Considerations and Limitations

In this article

Consider the following limitations for Veeam Data Cloud Vault:

* To back up to Veeam Data Cloud Vault from Veeam Backup & Replication and utilize Veeam Data Cloud Vault functionality you must meet the following prerequisites:

* Obtain Veeam Data Cloud Vault and configure its subscription. For more information, see the [Veeam Data Cloud Vault](https://helpcenter.veeam.com/docs/vdcv/userguide/welcome.html) User Guide.
* Have the License Administrator role. For more information, see this [Veeam KB article](https://www.veeam.com/kb2211).

|  |
| --- |
| Note |
| Ensure that the email address you use to access the My Account portal or the Veeam Data Cloud Vault portal matches the email address of the License Administrator. Consider that this email address is case-sensitive. If you plan to delegate access to another user, make sure that he also has the License Administrator role. |

* Make sure you have WebView2 Runtime installed on your backup server.
* You must enable encryption for every job that you target to Veeam Data Cloud Vault. For more information, see [Job Encryption](encryption_job.md).

|  |
| --- |
| Note |
| Job-level encryption is not required if you use Veeam Data Cloud Vault as a [capacity extent](capacity_tier.md) of a scale-out backup repository. |

* By default, [immutability](immutability_object_storage_repositories.md) is enabled for 30 days for Veeam Data Cloud Vault. You cannot disable immutability and cannot remove data during this period. You can modify the immutability period [when you configure Veeam Data Cloud Vault](veeam_data_cloud_details.md).
* If you [back up your configuration](backup_database.md), you must enable encryption for it. Otherwise, this option will be disabled when you configure Veeam Data Cloud Vault.
* Veeam Data Cloud Vault does not support China and Government regions.
* Veeam Data Cloud Vault supports the cool access tier only.
* You cannot use Veeam Data Cloud Vault as a source of [unstructured data backup](unstructured_data_backup.md).
* You cannot [move](capacity_tier_copy.md) or [copy](capacity_tier_copy.md) unencrypted backups to Veeam Data Cloud Vault.

* You must enable the capacity tier encryption for Veeam Data Cloud Vault if you want to use it as a capacity extent.

* You cannot [seed](data_box_seeding.md) data from the [Azure Data Box](osr_adding_data_box.md) device to Veeam Data Cloud Vault.
* [For backup jobs managed by Veeam Agent] You cannot back up data to Veeam Data Cloud Vault added in the direct connection mode.
* [For Veeam Cloud Connect] Veeam Data Cloud Vault cannot be used as a cloud repository in the direct connection mode.

Page updated 12/1/2025

Page content applies to build 13.0.1.1071
