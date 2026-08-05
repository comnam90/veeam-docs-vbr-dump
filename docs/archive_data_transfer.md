---
title: "Archive Tier Data Transfer"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archive_data_transfer.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Archive Tier Data Transfer


You can transfer outdated backup files from the performance tier or capacity tier to the archive tier. Depending on your scale-out backup repository configuration, data reaches the archive tier in one of two ways: through the capacity tier, or directly from the performance tier.

Transfer Through the Capacity Tier

If your scale-out backup repository includes the capacity tier, backup files reach the archive tier in two steps. First, Veeam Backup & Replication offloads them from the performance tier to the capacity tier, according to the policy you have selected (copy policy or move policy). Then, they move from the capacity tier to the archive tier. At this point, Veeam Backup & Replication always uses the move policy, since the archive tier does not support the copy policy to transfer data through the capacity tier. For more information about the capacity tier copy and move policies, see [Data Transfer for Capacity Tier](capacity_tier_data_transfer.md).

* If the capacity tier copy policy is enabled, the original file stays on the performance tier while Veeam Backup & Replication copies it to the capacity tier. When the archiving job runs, Veeam Backup & Replication moves that copy from the capacity tier to the archive tier.
* If the capacity tier move policy is enabled, Veeam Backup & Replication moves the file from the performance tier to the capacity tier. When the archiving job runs, Veeam Backup & Replication moves the file from the capacity tier to the archive tier.

Direct Transfer from the Performance Tier

If your scale-out backup repository has no capacity tier, you can archive backup files directly from the performance tier using the archive tier policies:

* Move policy — If you archive data directly from the performance tier using the move policy, Veeam Backup & Replication moves GFS backup files to the archive tier after they fall outside the archive window and deletes the local copies from the performance tier.
* Copy policy — If you archive data directly from the performance tier using the copy policy, Veeam Backup & Replication copies GFS backup files to the archive tier when they are created. The local copies remain on the performance tier until they fall outside the archive window. After that, Veeam Backup & Replication deletes them.

For more information, see [Archive Tier Policies](archive_tier_policies.md).

Page updated 2026-07-15

