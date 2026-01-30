---
title: "Configuring Archived Redo Log Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archived_redo_retention.html"
last_updated: "9/6/2023"
product_version: "13.0.1.1071"
---

# Configuring Archived Redo Log Retention


By default, archivelog deletion policy is disabled.

To configure archivelog deletion policy, run the following command. When the number of archived logs exceeds the specified number, RMAN deletes the oldest archived log.

|  |
| --- |
| CONFIGURE ARCHIVELOG DELETION POLICY TO BACKED UP 3 TIMES TO SBT; |

To delete obsolete archivelogs, run the following command. If you do not run this command, the archived logs will be deleted from the fast recovery area (FRA) only.

|  |
| --- |
| DELETE ARCHIVELOG ALL; |

To disable archivelog deletion policy, run the following command:

|  |
| --- |
| CONFIGURE ARCHIVELOG DELETION POLICY TO NONE; |

For details, see [this Oracle article](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmconfb.htm#BRADV89439).


