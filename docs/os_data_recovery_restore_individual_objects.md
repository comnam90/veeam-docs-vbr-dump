---
title: "Restoring Individual Objects or Versions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_data_recovery_restore_individual_objects.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Individual Objects or Versions


You can restore individual objects from the bucket or container backups to the original or a new location. This option can be useful, for example, if you need to get an older version of some objects from the backup.

When you restore specific objects, you can extract object versions not only from the backup repository, but also from the archive repository. For more information, see the [Restoring Objects from Archive Repository](os_data_recovery_restore_files_from_archive.md) section.

|  |
| --- |
| Note |
| Consider that from the archive repository you can restore objects only. Restore of prefixes from the long-term repository is not supported. |

Besides, you can restore multiple versions of the same object.

You can restore an entire object storage bucket in one of the following ways:

* [Restore individual objects or versions using console](os_data_recovery_restore_individual_objects_console.md).
* [Restore individual objects or versions using web UI](os_data_recovery_restore_individual_objects_web.md).

Page updated 2026-07-25

