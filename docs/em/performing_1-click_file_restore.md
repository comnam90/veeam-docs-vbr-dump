---
title: "Performing 1-Click File Restore"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/performing_1-click_file_restore.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Performing 1-Click File Restore


After you find the necessary files and folders, you can use Veeam Backup Enterprise Manager to restore them from backup with one click. You can choose to restore it to the original location or download it to the local machine.

|  |
| --- |
| Important |
| Consider the following:   * 1-Click file restore capability is available if you have the Enterprise or Enterprise Plus edition. * 1-Click file restore from a storage snapshot is not supported by Veeam Backup Enterprise Manager. |

Restore operations are only available to authorized users according to their security settings. Users with the Portal Administrator role can restore files both to the original location or download them to the local machine.

For users with the non-administrative roles, you can configure additional restriction settings. For example, you can prohibit restore operators to download files to the local machine so that they can restore files to the original location only. Additionally, you can specify the types of files that can be restored by operators (this can be helpful if you want to limit operators’ access to sensitive data). For details, see [Configuring Permissions for File and Application Item Restore](configuring_restrictions_for_restore.md).

|  |
| --- |
| Note |
| Consider the following:   * If you plan to restore a file from a machine backed up without guest indexing, consider that for restore operation this machine disk will be mounted directly from the backup in the repository to the mount server associated with that repository; when restoring from replica, it will be mounted to the backup server. When restoring from an indexed machine, no interim mount operations are needed. * If you want Veeam Backup Enterprise Manager to display symbolic links to folders when browsing through the machine file system at 1-click file restore, then you should enable indexing in the backup job for that machine (running Linux or another non-Windows OS). |

In This Section

* [Restoring Files to the Original Location](restoring_to_original_location.md)
* [Downloading Files to the Local Machine](downloading_files_to_local_machine.md)
* [Using Restore Lists](restoring_multiple_files.md)


