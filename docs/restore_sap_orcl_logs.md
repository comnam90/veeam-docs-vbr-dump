---
title: "Restore Redo Logs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_sap_orcl_logs.html"
last_updated: "3/14/2024"
product_version: "13.0.1.1071"
---

# Restore Redo Logs

In this article

If you want to restore redo log files that were backed up with BRARCHIVE, you can use the BRRESTORE tool. For details, see [this SAP article](https://help.sap.com/doc/saphelp_nwpi71/7.1/en-US/46/bafec999701515e10000000a114a6b/frameset.htm).

Example: Performing Restore of SAP on Oracle Redo Logs

|  |
| --- |
| brrestore -d util\_file -p $Oracle\_HOME/dbs/veeam\_initSID.sap -a 1-100 |

Run the brrestore command with the following parameters:

1. Depending on which backup you want to restore from, use the util\_file or rman\_util option as the argument for the -d (-device) parameter. If the backup was created by Backint, use util\_file. If the backup was created by RMAN, use rman\_util.
2. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.
3. Specify the log sequence number interval as the argument for the -a (-archive) parameter. This option defines which log files must be restored.

Page updated 3/14/2024

Page content applies to build 13.0.1.1071
