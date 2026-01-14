---
title: "Database Protection"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_sap_orcl.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Database Protection

In this article

After you configure Veeam Plug-In for SAP on Oracle, you can back up databases using SAP BR\*Tools. Veeam Plug-In will automatically transfer backup files to a backup repository and store them in the Veeam proprietary format. The backup process itself is performed by SAP BR\*Tools.

Keep in mind that examples in this section are provided only for demonstrating purposes. For details on full backup functionality of SAP BR\*Tools, see [this SAP article](https://help.sap.com/doc/saphelp_nw74/7.4.16/en-us/46/e42438f63966c6e10000000a1553f7/content.htm?loaded_from_frameset=true).

In This Section

* [Considerations and Limitations](sap_orcl_backup_limitations.md)
* [SAP on Oracle Backup Using Backint](backup_brbackup.md)
* [SAP on Oracle Backup Using RMAN\_UTIL](rman_util.md)
* [Backup Job in Veeam Backup & Replication](backup_job_vbr.md)

|  |
| --- |
| Note |
| This guide provides examples for SAP BR\*Tools commands. Apart from BR\*Tools scripts, you can perform backup operations using BRTOOLS interactive wizard and BR\*Tools Studio. For details, see [this SAP article](https://help.sap.com/doc/saphelp_nw73ehp1/7.31.19/en-US/47/15f47c634b63efe10000000a114a6b/frameset.htm). |

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
