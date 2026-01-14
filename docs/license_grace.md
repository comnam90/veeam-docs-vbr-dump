---
title: "License Expiration"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/license_grace.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# License Expiration

In this article

When the license expires, Veeam Backup & Replication behaves in the following way depending on the license type:

* Evaluation and NFR licenses: Veeam Backup & Replication will stop processing workloads.
* Paid licenses: Veeam Backup & Replication will switch to the grace period.
* Promo license: Veeam Backup & Replication will remove the granted instances and stop processing workloads for them. Promo license does not have a grace period. Upon expiration of the primary license, the promo license will also expire, regardless of its own expiration date.

Perpetual Socket and Perpetual Instance licenses do not expire. However, such licenses have support expiration date. Veeam Backup & Replication will inform you about the support expiration date.

Grace Period

To ensure a smooth license update and provide sufficient time to install a new license file, Veeam Backup & Replication offers a grace period. Grace period is available for paid licenses.

During the grace period, you can perform all types of data protection and disaster recovery operations. However, Veeam Backup & Replication will inform you about the license expiration when you open the Veeam Backup & Replication console. The license status in the License Information window will appear as Expired.

You must update your license before the end of the grace period. If you do not update the license, Veeam Backup & Replication stops processing workloads. All existing jobs fail with the Error status. However, you will be able to restore machine data from existing backups.

Grace Period Duration

Before the license expires, Veeam Backup & Replication notifies you about soon license expiration.

The number of days for notification and grace period depends on the type of license:

| License Type | License Expiration Notification | Grace Period |
| --- | --- | --- |
| Subscription | 30 days | 30 days |
| Perpetual | 14 days before Support expiration date | n/a |
| Perpetual | 14 days before Support expiration date | n/a |
| Rental | 7 days | 60 days |
| Evaluation | 30 days | 0 days |
| NFR | 30 days | 0 days |
| Promo | 7 days | n/a |

Switching to Veeam Backup & Replication Community Edition

If you do not want to renew your license, you can switch to the free product version named Veeam Backup & Replication Community (free) Edition. For more information, see [Veeam Backup & Replication Community Edition](https://www.veeam.com/virtual-machine-backup-solution-free.html).

To do so, remove your license. For more information, see [Removing License](removing_license.md).

Expiration of Merged Licenses

When the merged license expires, Veeam Backup & Replication stops processing workloads after the grace period.

If you merged licenses with different expiration dates, the merged license will expire on the date that is closer. For example, if you merged a Perpetual license and a Subscription license, the expiration date will be inherited from the Subscription license.

In such case, you can update your Subscription license or continue using the Perpetual license. To continue using the Perpetual license, remove the Subscription license. For more information, see [Removing License](removing_license.md).

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
