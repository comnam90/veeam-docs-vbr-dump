---
title: "How Veeam Plug-In for SAP MaxDB Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_overview_hiw.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# How Veeam Plug-In for SAP MaxDB Works


With the configured Veeam Plug-In for SAP MaxDB, you can use SAP MaxDB to perform backup and restore operations. Veeam Plug-In functions as a link between SAP MaxDB infrastructure and Veeam backup repositories. Veeam Plug-In accepts some commands from SAP MaxDB Database Manager and performs backup or restore tasks.

Veeam Plug-In for SAP MaxDB consists of the following components:

* Veeam Backint is a component that triggers a backup process to the Veeam backup repository when you run the built-in command intended to back up SAP MaxDB.
* SapMaxDBBackintManager is a component that communicates with the Veeam Backup & Replication server and starts data movers.
* SapMaxDBBackintConfigTool is a component that allows to configure Veeam Plug-In and save the configuration to a file.
* Veeam Data Mover is a component that transfers data to the Veeam backup repositories.

How Backup Operations Work

After you configure Veeam Plug-In for SAP MaxDB, components work in the following way:

1. When you launch a database backup, SAP MaxDB Database Manager starts the data transfer and commands Veeam Backint to start the services of Veeam Plug-In. Veeam Plug-In services are necessary to back up data.
2. SapMaxDBBackintManager connects to the Veeam Backup & Replication server and creates a backup job object (if it has not been created before). Veeam Backup & Replication administrators can use this backup job object to monitor the backup process, manage backup files and copy the database backup to secondary repositories.
3. Veeam Plug-In starts Veeam Data Mover on the SAP MaxDB server and on the backup repository. Veeam Data Movers create communication channels for each backup data stream. Depending on the number of channels specified in Veeam Plug-In settings, there can be 1 or up to 32 parallel channels.
4. Veeam Data Movers transport database backup files to the backup repository.


