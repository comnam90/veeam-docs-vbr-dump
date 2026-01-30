---
title: "Storage Snapshots on BitLocker Encrypted Volumes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_storage_snapshots_encrypted.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# Storage Snapshots on BitLocker Encrypted Volumes


You can use Veeam Backup & Replication and Veeam Agent for Microsoft Windows operating in the managed mode to create backups from storage snapshots located on volumes encrypted with Microsoft Windows BitLocker.

If volumes you want to back up are protected by Microsoft Windows BitLocker, do the following:

1. On the Veeam Agent computer, set BitLocker to automatically unlock volumes to which LUNs are mapped. To learn more, see [Microsoft documentation](https://learn.microsoft.com/en-us/powershell/module/bitlocker/enable-bitlockerautounlock?view=windowsserver2022-ps).
2. On the backup proxy, perform the following operations:

1. Connect volumes to which LUNs are mapped to the backup proxy.
2. Set BitLocker to automatically unlock connected volumes on the backup proxy. To learn more, see [Microsoft documentation](https://learn.microsoft.com/en-us/powershell/module/bitlocker/enable-bitlockerautounlock?view=windowsserver2022-ps).
3. Disconnect volumes to which LUNs are mapped from the backup proxy.

If you plan to use several backup proxies, repeat step 2 for each backup proxy.

Consider the following:

* Automatic unlocking requires encryption of the system drive.

* If automatic unlocking is not set on the Veeam Agent computer, file indexing will not work during the backup process.
* If automatic unlocking is not set on the backup proxy, only volume-level restore to a new location is available. File-level restore and volume-level restore to the original location will fail.


