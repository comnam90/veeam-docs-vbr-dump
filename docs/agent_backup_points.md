---
title: "Managing Backup Files and Restore Points"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_backup_points.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Managing Backup Files and Restore Points


In the [Backup Properties](agent_backup_properties.md#parent) and [Agent Backup Properties](agent_backup_properties.md#child) windows, you can can perform the following actions:

* [Change the malware status of backup files](#status).
* [Copy the path to the required backup file](#copy).
* [Remove records about missing backup files from the configuration database and delete backup files](#remove).

Any actions on backup files will also apply to related restore points.

Changing Malware Status

|  |
| --- |
| NOTE |
| This option is available only for backups created with Veeam Agent for Microsoft Windows or Veeam Agent for Linux. |

You can manually change the malware status of backup files. To do this, right-click the required backup file in the Files section and select one of the following options depending on the current malware status:

* Malware > Mark as clean — if you cleaned the Veeam Agent computer from malware or the malware detection event was false positive.
* Malware > Mark as infected — if you a specific backup file is infected but the malware detection scan did not detect any suspicious activity.

Alternatively, you can select the required backup file and click Malware > Mark as clean or Malware > Mark as infected on the ribbon.

|  |
| --- |
| NOTE |
| If you set the malware status of the restore point manually, it will have a higher priority. The result of the malware detection scan will not affect the malware status of this restore point even if the malware detection event is created. |

To learn more about the malware detection feature, see [Malware Detection](malware_detection.md).

Copying Path to Backup File

|  |
| --- |
| NOTE |
| Consider the following:   * The option is available if you are viewing the [properties of the entire backup](agent_backup_properties.md#parent). * The option is not available for backups stored in the Veeam Cloud Connect repository. * When you copy the path to the backup file stored in the object storage repository, only the name of the backup file is copied. |

You can copy the path to the required backup file. To do this, right-click the required backup file in the Files section and select Copy path or select the backup file and click Copy path on the ribbon.

Removing Backup Files

In some cases, one or more backup files in the backup chain may be inaccessible. It can happen, for example, if the backup repository is put into Maintenance mode (for scale-out backup repositories), the backup repository is unavailable, or some backup file is missing in the backup chain. Backup chains that contain inaccessible backup files get corrupted — you cannot perform backup or restore data from the restore points related to inaccessible backup files and restore points that depend on such restore points.

Inaccessible backup files are displayed in the Files section in italics.

You can perform the following operations with inaccessible backup files:

* Forget — if you want to remove records about inaccessible backup files from the configuration database. Veeam Backup & Replication will “forget” about inaccessible backup files and will not display them in the console. If backup files are still available, they will remain on disk.

To remove records about inaccessible backup files from the configuration database, right-click the inaccessible backup file and select Forget.

* To remove only the selected backup file and backup files and restore points that depend on it, select This backup and dependent backups.
* To remove all inaccessible backup files and backup files and restore points that depend on them, select All unavailable backups.

Alternatively, you can select the required backup file and click Forget > This backup and dependent backups or Forget > All unavailable backups on the ribbon.

* Remove — if you want to remove records about inaccessible backup files from the configuration database and delete backup files from disk (if backup files are still available).

To remove inaccessible backup files from the configuration database and disk, right-click the inaccessible backup file and select Remove from disk.

* To remove only the selected backup file and backup files and restore points that depend on it, select This backup and dependent backups.
* To remove all inaccessible backup files and backup files and restore points that depend on them, select All unavailable backups.

Alternatively, you can select the required backup file and click Remove from disk > This backup and dependent backups or Remove from disk > All unavailable backups on the ribbon.

|  |
| --- |
| TIP |
| The Forget and Remove from disk options are available only for the backup files missing from the backup chain or backup files that depend on missing ones. If the backup file is available in the backup chain and does not depend on a missing backup file, you will not be able to use the Forget and Remove from disk options for it. |

To learn more, see [Removing Missing Restore Points](remove_missing_point.md).


