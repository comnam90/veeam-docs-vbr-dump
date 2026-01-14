---
title: "Restore of Control File from Autobackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/controlfile_restore.html"
last_updated: "3/28/2025"
product_version: "13.0.1.1071"
---

# Restore of Control File from Autobackup

In this article

You may need to restore the Oracle database control file in the following cases:

* If you want to restore the database to a new location where the control file does not exist.
* If the database control file is lost or corrupted.

If you use Veeam Plug-In for Oracle RMAN and want to restore the Oracle database control file from autobackup, the autobackup format must be set to the SBT\_TAPE device type.

To check if persistent configuration for the control file autobackup format is set to the SBT\_TAPE device type, you can run the SHOW ALL or SHOW CONTROLFILE AUTOBACKUP FORMAT commands in the RMAN console. If the persistent configuration is set, you don't need to set the control file autobackup format before the restore command. If it is not set, you must run the SET CONTROLFILE AUTOBACKUP command before the restore process. For more information, see [Example 1. Restoring Control File if Persistent Configuration Setting Is NOT Set](#notset).

If you do not have the autobackup file name for the restore script, you can restore using the creation date of the autobackup file. For more information, see [Example 3. Restoring Control File Without Autobackup File Name](#noname).

|  |
| --- |
| Note |
| To restore the control file from autobackup, the database must be in the NOMOUNT state. |

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Control File if Persistent Configuration Setting is NOT Set

|  |  |  |
| --- | --- | --- |
| If the persistent configuration for the control file autobackup format is not set to the SBT\_TAPE device type, you must set the autobackup format before running the control file restore. To do this, run one of the following scripts, depending on your OS.   * For Linux and Unix machines:   |  | | --- | | RUN {  ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so';  SET CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE 'SBT\_TAPE' TO '%F\_RMAN\_AUTOBACKUP.vab';  RESTORE controlfile FROM 'c-4097408439-20200410-00\_RMAN\_AUTOBACKUP.vab';  }  EXIT; |   * For Microsoft Windows machines:   |  | | --- | | RUN {  ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=%PROGRAMFILES%\Veeam\VEEAMP~2\ORACLE~2.DLL';  SET CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE 'SBT\_TAPE' TO '%F\_RMAN\_AUTOBACKUP.vab';  RESTORE controlfile FROM 'c-4097408439-20200410-00\_RMAN\_AUTOBACKUP.vab';  }  EXIT; | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Control File if Persistent Configuration Setting is Set

|  |  |  |
| --- | --- | --- |
| If persistent configuration for the control file autobackup format is set to the SBT\_TAPE device type, you can restore with one of the following scripts, depending on your OS.   * For Linux and Unix machines:   |  | | --- | | RUN {  ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so';  RESTORE controlfile FROM 'c-4097408439-20200410-00\_RMAN\_AUTOBACKUP.vab';  }  EXIT; |   * For Microsoft Windows machines:   |  | | --- | | RUN {  ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=%PROGRAMFILES%\Veeam\VEEAMP~2\ORACLE~2.DLL';  RESTORE controlfile FROM 'c-4097408439-20200410-00\_RMAN\_AUTOBACKUP.vab';  }  EXIT; | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Control File Without Autobackup File Name

|  |  |  |
| --- | --- | --- |
| If you do not have the autobackup file name to include in the restore script, you can set RMAN to search for the autobackup file within a certain time period. In this case, you must set the database ID (DBID) before you restore. To learn how to find DBID, see [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/19/bradv/rman-complete-database-recovery.html#GUID-34BB2E4B-B2FC-4701-BB65-BFED027DB865).  Using one of the example scripts below, depending on your OS, you can search for the autobackup file that was created yesterday. If such autobackup file is not detected, RMAN will search for autobackup files that were created earlier, up to 30 days ago.  Keep in mind that the example below is applicable only if persistent configuration for the control file autobackup format is set to the SBT\_TAPE device type.   * For Linux and Unix machines:   |  | | --- | | RUN { |   * For Microsoft Windows machines:   |  | | --- | | RUN {  ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=%PROGRAMFILES%\Veeam\VEEAMP~2\ORACLE~2.DLL'; RESTORE until time 'sysdate-1' CONTROLFILE FROM AUTOBACKUP maxdays 30; } EXIT; |  Once the autobackup file is detected, RMAN uses it to restore the control file. |

See Also

If you did not find an example that suits your needs, refer to Oracle documentation:

* For details on restoring the control file, see [this Oracle article](https://docs.oracle.com/cd/B19306_01/backup.102/b14192/recov004.htm#CFABADJC).
* For details on the control file autobackup format, see [this Oracle article](https://docs.oracle.com/cd/B19306_01/backup.102/b14192/setup004.htm#i1017907).

Page updated 3/28/2025

Page content applies to build 13.0.1.1071
