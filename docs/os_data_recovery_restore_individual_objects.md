---
title: "Restoring Individual Objects or Versions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_data_recovery_restore_individual_objects.html"
last_updated: "12/19/2023"
product_version: "13.0.1.1071"
---

# Restoring Individual Objects or Versions

In this article

You can restore individual objects from the bucket or container backups to the original or a new location. This option can be useful, for example, if you need to get an older version of some objects from the backup.

When you restore specific objects, you can extract object versions not only from the backup repository, but also from the archive repository. For more information, see the [Restoring Objects from Archive Repository](os_data_recovery_restore_files_from_archive.md) section.

|  |
| --- |
| Note |
| Consider that from the archive repository you can restore objects only. Restore of prefixes from the long-term repository is not supported. |

Besides, you can restore multiple versions of the same object.

Before you restore specific objects, [check prerequisites](restore_individual_objects_byb.md). Then use the Objects or Versions Restore wizard to restore objects or their specific versions.

1. [Launch the Objects or Versions Restore wizard](restore_individual_objects_launch.md).
2. [Select an object to restore](restore_individual_objects_backup.md).
3. [Verify object restore settings](restore_individual_objects_summary.md).
4. [Select objects to restore](restore_individual_objects_browser.md).
5. [Select a restore mode](restore_individual_objects_restore_mode.md).
6. [Select a restore point](restore_individual_objects_restore_point.md).
7. [Select an object version to restore](restore_individual_objects_object_version.md).
8. [Specify the destination for object restore](restore_individual_objects_destination.md).
9. [Finish working with the wizard](restore_individual_objects_summary_finish.md).

Page updated 12/19/2023

Page content applies to build 13.0.1.1071
