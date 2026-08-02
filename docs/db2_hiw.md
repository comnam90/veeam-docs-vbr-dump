---
title: "How Veeam Plug-In for IBM Db2 Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Veeam Plug-In for IBM Db2 Works


Veeam Plug-In acts as an agent between an IBM Db2 server and Veeam backup repositories.

Veeam Plug-In compresses database backups and transfers them to a backup repository connected to the Veeam Backup & Replication infrastructure. After you install and configure Veeam Plug-In on the IBM Db2 server, you can perform all backup and restore operations with scripts and with IBM Db2 tools, such as native IBM Db2 Call Level Interface (CLI).

When Veeam Plug-In is configured, IBM Db2 tools perform a database backup in the following way:

1. When you start a database backup, IBM Db2 loads the configuration provided by Veeam Plug-In. This configuration is stored in the Veeam Plug-In configuration file (veeam\_config.xml) that is located in the following location depending on the OS running on the machine where Veeam Plug-In is installed:

1. For Linux or Unix: /opt/veeam/VeeamPluginforDB2/veeam\_config.xml

1. For Microsoft Windows: %PROGRAMFILES%\Veeam\VeeamPluginforDB2\veeam\_config.xml

1. Veeam Plug-In connects to the backup server specified in the configuration file and creates a backup job. In the Veeam Backup & Replication console, Veeam backup administrators can use the backup job to monitor IBM Db2 backups. Keep in mind that all backup jobs that you run on your machine with Veeam Plug-In are displayed as 1 backup job in the Veeam Backup & Replication console.
2. Veeam Plug-In starts Veeam Data Mover services on the IBM Db2 server and on a backup repository.
3. Veeam Data Movers transport data to the backup repository.

[![How Veeam Plug-in for IBM Db2 Works](images/plugins_db2_plugin_architecture.webp)](images/plugins_db2_plugin_architecture.webp "How Veeam Plug-in for IBM Db2 Works")

Page updated 2026-07-02

