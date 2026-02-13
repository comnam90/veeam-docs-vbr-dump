---
title: "Deleting Backups Using IBM Db2 Tools"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_retention_remove_from_machine.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Deleting Backups Using IBM Db2 Tools


To delete backups, you can use the IBM Db2 built-in option: the PRUNE HISTORY command. To learn more about the command, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=commands-prune-historylogfile).

|  |
| --- |
| Important |
| To delete backups using the PRUNE HISTORY command, you must set the AUTO\_DEL\_REC\_OBJ parameter before you create backups. For details, see [Preparing Database](db2_protection_prepare.md#increment). |

To delete backup files and log archives from the backup repository, use the following command:

|  |
| --- |
| db2 prune history <timestamp> and delete |

where <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format.

With this command, Veeam Plug-In will delete all backup files up to the time that you specified in the command. Thus, Veeam Plug-In will not delete the backup with the time stamp that you specified. Also, the PRUNE HISTORY command will not delete to the most recent full backup and associated objects. For example, incremental and log backups.

If you want to delete the most recent full backup and associated objects, use the WITH FORCE OPTION option with the PRUNE HISTORY command:

|  |
| --- |
| db2 prune history <timestamp> with force option and delete |

where <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format.

With this command, Veeam Plug-In will delete all backup files up to the time and equal the time that you specified in the command. Thus, Veeam Plug-In will also delete the backup with the time stamp that you specified from the backup repository. Veeam Plug-In will also delete the most recent full backup and associated objects.


