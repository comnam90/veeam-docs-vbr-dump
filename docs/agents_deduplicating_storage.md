---
title: "Backup to Deduplicating Storage Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_deduplicating_storage.html"
last_updated: "8/5/2025"
product_version: "13.0.1.1071"
---

# Backup to Deduplicating Storage Appliances


You can store backups in the deduplicating storage appliances added as backup repositories. To learn the full lists of supported appliances and their requirements and limitations, see [Deduplicating Storage Appliances](deduplicating_storage_appliances.md).

If you want to use immutability with the deduplicating storage appliances, consider the limitations listed in the following subsections:

* [HPE StoreOnce Immutability and Veeam Agents](#so).
* [Dell Data Domain Immutability and Veeam Agents](#dd).

HPE StoreOnce Immutability and Veeam Agents

If you want to use immutability with HPE StoreOnce Catalyst repositories, make sure that the values of the following settings configured in Veeam Backup & Replication do not exceed the Maximum ISV Controlled Data Retention setting in HPE StoreOnce:

* The immutability period specified in the backup repository settings.
* The long-term retention period configured in backup job settings.

If the value of at least one of these periods exceeds the maximum value set for immutability in HPE StoreOnce Catalyst Store, consider the following:

* If the immutability period specified in the backup repository settings exceeds the maximum value set for immutability in HPE StoreOnce Catalyst Store, Veeam Backup & Replication applies immutability to the created backups according to the maximum value set for immutability in HPE StoreOnce Catalyst Store.

* If the long-term retention period configured in backup job settings exceeds the maximum value set for immutability in HPE StoreOnce Catalyst Store, the immutability period for backups with GFS flags is set according to the maximum value set for immutability in HPE StoreOnce Catalyst Store. For example, if the backup is stored for 1 year, but the maximum value for immutability in HPE StoreOnce Catalyst Store is set to 6 months, the backups will be immutable for 6 months.

To learn more about immutability for the HPE StoreOnce Catalyst repositories, see [HPE StoreOnce and Immutability](deduplicating_appliance_storeonce.md).

Dell Data Domain Immutability and Veeam Agents

If you want to use immutability with the Dell Data Domain backup repository, make sure that the values of the following settings configured in Veeam Backup & Replication lie in the range between the minimum and maximum retention periods configured in Dell Data Domain:

* The immutability period specified in the backup repository settings.
* The long-term retention period configured in backup job settings.

The minimum and maximum values are included into the range.

If the value of at least one of these periods lies outside the established range, consider the following:

* If the immutability period specified in the backup repository settings lies outside the range between the minimum and maximum retention periods configured in Dell Data Domain, the immutability for backups is set equal to the nearest range value.
* If the long-term retention period configured in backup job settings lies outside the range between the minimum and maximum retention periods configured in Dell Data Domain, the immutability period for backups with GFS flags is set equal to the nearest range value. For example, if the backup is stored for 1 year, but the range for immutability in Dell Data Domain is set to from 2 to 6 months, the backups will be immutable for 6 months.

To learn more about immutability for the Dell Data Domain backup repositories, see [Retention Lock](dell_dd_supported_features.md).


