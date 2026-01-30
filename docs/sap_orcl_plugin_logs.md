---
title: "Logs and Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_plugin_logs.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Logs and Support


If you have any questions or issues with Veeam Plug-In for SAP on Oracle or Veeam Backup & Replication, you can search for a resolution on [Veeam Community Forums](https://forums.veeam.com/) or submit a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html).

When you submit a support case, we recommend that you attach log files related to Veeam Plug-In operations.

Veeam Plug-In Logs

To export Veeam Plug-In logs, do the following:

1. On the Veeam Backup & Replication server, go to %PROGRAMDATA%\Veeam\Backup\Plugin.
2. Copy logs of the required backup or restore process.

SAP Backint Logs

To export SAP Backint logs, on the SAP on Oracle server, go to /tmp/veeam\_plugin\_logs/<user\_name>/ and copy the following files:

* SapOracleBackint.log
* SapBackintOracleManager.log
* Agent.Source.log

BRTools Logs

The Detail and Summary logs of BRTools are stored in the /oracle/SID/sapbackup and /oracle/SID/saparch directories.

For details, see the following SAP articles:

* [BRBACKUP Logs](https://help.sap.com/viewer/3ef1b95cacbf4f77a066797285371bb9/118/en-US/471e21a1e83612b8e10000000a1553f7.html)
* [BRRESTORE Logs](https://help.sap.com/viewer/3ef1b95cacbf4f77a066797285371bb9/118/en-US/472385249a59550ee10000000a114a6b.html)
* [BRARCHIVE Logs](https://help.sap.com/viewer/3ef1b95cacbf4f77a066797285371bb9/118/en-US/47231bb19a0c550fe10000000a114a6b.html)
* [BRRECOVER Logs](https://help.sap.com/viewer/3ef1b95cacbf4f77a066797285371bb9/118/en-US/472387629a59550ee10000000a114a6b.html)


