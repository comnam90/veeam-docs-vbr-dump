---
title: "Configuring Retention Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/retention_rman_config.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Configuring Retention Policy


If you want to edit a retention policy for Oracle RMAN backups, you must connect to the target database in RMAN console and configure one of the following retention policies:

* Redundancy-Based Retention: The redundancy parameter specifies how many full or level 0 backups of each data file and control file should RMAN keep in the repository. If the number of backups exceeds the specified value, RMAN considers the oldest backups as obsolete. By default, the redundancy parameter is set to 1. To configure a redundancy-based retention policy, run the following command:

|  |
| --- |
| CONFIGURE RETENTION POLICY TO REDUNDANCY 7; |

* Recovery Window-Based Retention: The recovery window parameter specifies the number of days between the current time and the earliest point of recoverability. RMAN does not consider any full or level 0 incremental backups as obsolete if it falls within the recovery window. To configure a window-based retention policy, run the following command:

|  |
| --- |
| CONFIGURE RETENTION POLICY TO RECOVERY WINDOW OF 7 days; |

|  |
| --- |
| Note |
| Make sure that the value set for the CONTROL\_FILE\_RECORD\_KEEP\_TIME parameter in the control file is greater than the recovery window. Otherwise, the retention policy will not be applicable as the backup records will be always overwritten earlier than they can be considered obsolete by the retention policy. To learn more, see [this Oracle article](https://support.oracle.com/knowledge/Oracle%20Database%20Products/397269_1.html) (requires an Oracle Support account). |

Deleting Obsolete Backups

To delete obsolete backups, run the following command after each backup:

|  |
| --- |
| DELETE OBSOLETE; |

Disabling Retention Policy

To disable retention policy for RMAN backups, run the following command:

|  |
| --- |
| CONFIGURE RETENTION POLICY TO NONE; |

For details, see [this Oracle article](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmconfb.htm#BRADV8400).


