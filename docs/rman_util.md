---
title: "SAP on Oracle Backup Using RMAN\_UTIL"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_util.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# SAP on Oracle Backup Using RMAN\_UTIL


The rman\_util parameter allows you to back up Oracle databases using Oracle RMAN in combination with [Veeam Plug-In for Oracle RMAN](rman_plugin.md). BACKINT

Prerequisites

|  |
| --- |
| Important |
| * Before you back up the Oracle database with the rman\_util parameter, you must [install and configure Veeam Plug-In for Oracle RMAN](rman_plugin_deployment.md) on the SAP on Oracle server. * See [Limitations and Considerations](sap_orcl_backup_limitations.md). |

When you perform the backup using the RMAN\_UTIL, RMAN\_STAGE or RMAN\_DISK parameter, by default, BR\*Tools creates one backup set for each log or datafile. This means that every backup piece will contain only one file. This results in a large amount of backup files and significantly slows down backup and restore processes. To avoid this problem, do the following:

1. In the SAP on Oracle server, open the /oracle/ODB/sapprof/veeam\_initSID.sap file using a text editor.
2. Change the default values for the following parameters:

|  |
| --- |
| rman\_filesperset = 10  rman\_filesperset\_arch = 100 |

For example: set the rman\_filesperset value to 10 for datafiles and the rman\_filesperset\_arch value to 100 for logs.

Also, you must add the SBT\_LIBRARY directory to the rman\_parms setting in the veeam\_initSID.sap file:

1. In the SAP on Oracle server, open the /oracle/ODB/sapprof/veeam\_initSID.sap file using a text editor.

1. Add the following line in the veeam\_initSID.sap file:

|  |
| --- |
| rman\_parms = 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' |

How SAP on Oracle Backup Using RMAN\_UTIL Works

When you launch the BRBACKUP or BRARCHIVE tool with the RMAN\_UTIL parameter, the following happens:

1. SAP BR\*Tools launches the RMAN backup script.
2. Oracle RMAN launches Veeam Plug-In for Oracle RMAN services.
3. Oracle RMAN starts the backup process:

1. Veeam Plug-In compresses database backup files or redo logs and sends them to the target backup repository through one or multiple channels.
2. Veeam Plug-In for Oracle RMAN connects to Veeam Backup & Replication and creates a backup job object that shows the job progress and logs.

1. BR\*Tools launches the Veeam Plug-In for SAP on Oracle services.
2. BR\*Tools start the control data files backup:

1. Control file, BR\*Tools logs are compressed and sent to a backup repository.

1. Veeam Plug-In for SAP on Oracle connects to Veeam Backup & Replication and creates a backup job object that shows the job progress and logs.


