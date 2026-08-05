---
title: "Get Backup Time Stamp"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_get_time_stamp.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get Backup Time Stamp


To restore IBM Db2 databases from a backup, you need a backup time stamp. IBM Db2 generates a time stamp for each backup in the yyyymmddhhmmss format. Using this timestamp, Veeam Plug-In restores the database from the backup file created at the certain time.

To get backup details, run the --get-restore-points command. Depending on the OS you are using, run one of the following commands:

* For Linux or Unix:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --get-restore-points --time-range <time\_period> --database <database\_name> --json > <timestamps.json> |

* For Microsoft Windows:

|  |
| --- |
| "C:\Program Files\Veeam\VeeamPluginforDB2\DB2ConfigTool.exe" --get-restore-points --time-range <time\_period> --database <database\_name> --json > <timestamps.json> |

where:

* <time\_period> is the time period when the backup you need was created. You must specify this value in a time stamp format. For details, see [Command Parameters](#params).
* <database\_name> is the name of a database whose backups you need.
* <timestamps.json> is the name of a .JSON file with the command output.

If the command run is successful, Veeam Plug-In provides the following details of your machine backups that are available in the connected backup repository:

* Database instance name
* Database name
* Partition number
* Time stamp
* Backup type. Possible values:

* Full
* Incremental
* Delta

Command Parameters

You can specify the following parameters for the --get-restore-points command:

Command Parameters

| Parameter | Description |
| --help | Shows the list of parameters for the --get-restore-points command. |
| --time-range | Defines the time period when the backup was created. Veeam Plug-In will return the list of backups created within the specified period.  Using the --time-range parameter, you can select the level of details for a time stamp from yyyymm to yyyymmddhhmmss. For example, if you use following time stamp, Veeam Plug-In will return the list of backups created within a certain hour: 2024052417. |
| --database | This parameter is optional. Defines the name of the backed-up database. Veeam Plug-In will return the list of backups only of the specified database. |
| --json | This parameter is optional. If you use this parameter, Veeam Plug-In create a .JSON file in your current directory and collect the command output in this file. |

Page updated 2026-07-02

