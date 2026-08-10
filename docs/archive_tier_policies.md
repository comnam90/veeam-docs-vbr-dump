---
title: "Archive Tier Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archive_tier_policies.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Archive Tier Policies


When you configure an archive tier, you can choose the copy policy, the move policy, or a combination of both to define how Veeam Backup & Replication transfers GFS backups to the archive extent.

Copy policy

When you enable the copy policy, Veeam Backup & Replication copies backup files to the archive extent at the next archiving job run after they are created on the performance tier. By default, the archiving job runs every 4 hours. Veeam Backup & Replication does not immediately remove backup files from the performance tier — local copies remain there until they exceed the retention policy period. If immutability is enabled, Veeam Backup & Replication deletes them only after the immutability period expires.

|  |
| --- |
| Important |
| The copy policy is available only for direct data transfer from the performance tier to the archive tier. If the scale-out backup repository includes a capacity tier, only the move policy is available. |

Move policy

When you enable the move policy, Veeam Backup & Replication moves backup files to the archive extent when they belong to the inactive backup chain and exceed the archive window period. The archive window period is the number of days after which Veeam Backup & Replication removes the backup file from the performance and capacity tier and moves it to the archive tier. You can specify the archive window period in the [archive tier](new_archive_tier.md#archivewindow) settings. Once the backup file becomes older than N days, Veeam Backup & Replication moves this backup file to the archive tier and removes the original backup file from the source extent.

Combining Move and Copy Policies

You can enable both policies at the same time. In this case, Veeam Backup & Replication copies each backup file to the archive extent at the next archiving job run after its creation on the performance tier. The local copy remains on the performance tier until it exceeds the archive window period. Once the archive window period expires, Veeam Backup & Replication deletes the local copy, while the archived copy remains in the archive extent.

Page updated 2026-07-23

