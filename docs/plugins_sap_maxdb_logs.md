---
title: "Logs and Support"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_logs.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# Logs and Support

In this article

If you have any questions or issues with Veeam Plug-In for SAP MaxDB or Veeam Backup & Replication, you can search for a resolution on [Veeam Community Forums](https://forums.veeam.com/) or submit a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, we recommend that you attach the following logs:

* [Veeam Plug-In logs](#vp)
* [SAP MaxDB logs](#db)
* [SAP Backint logs](#backint)

Veeam Plug-In Logs

To export Veeam Plug-In logs, on the Veeam Backup & Replication server, go to %PROGRAMDATA%\Veeam\Backup\Plugin and copy logs of the required backup or restore process.

SAP MaxDB Logs

To export the SAP MaxDB log files, navigate to the database home folder on the SAP MaxDB server and copy the following files:

* dbm.ebp
* dbm.ebl
* dbm.ebf
* dbm.mdf
* dbm.knl
* dbm.prt
* dbm.ins
* KnlMsg
* KnlMsg.old
* KnlMsgArchive
* knltrace
* dbm.cfg
* dbm.upc
* bsi.env
* adapter\_config.par

Keep in mind that the listed files may be located in different directories depending on the initial SAP MaxDB installation and database name.

For example:

|  |
| --- |
| /sapdb/MAXDB1/data/wrk/MAXDB1 |

SAP Backint Logs

To export SAP Backint logs, navigate to Veeam logs directory: /tmp/veeam\_plugin\_logs/, and copy the following files from /root and /sdb user folders:

* /root/SapBackintMaxDBManager.log
* /root/SAPMaxDBConfigTool.log

* /sdb/Agent.Source.log
* /sdb/SapBackintMaxDBManager.log
* /sdb/SapMaxDBBackint.log

Page updated 12/17/2025

Page content applies to build 13.0.1.1071
