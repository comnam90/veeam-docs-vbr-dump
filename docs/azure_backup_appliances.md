---
title: "Backup Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_backup_appliances.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Appliances


A backup appliance is a Linux-based Azure VM where Veeam Backup for Microsoft Azure is installed.

If you have multiple backup appliances in Microsoft Azure, you can add the appliances to Veeam Backup & Replication, and then use the Veeam Backup & Replication console as the central management console for backup appliance operations. For more information on the Veeam Backup & Replication console, see [Backup & Replication Console](backup_console.md).

Backup Appliance Software

The Azure VM running Veeam Backup for Microsoft Azure is deployed with the pre-installed set of software components:

* Ubuntu 22.04 LTS
* ASP.NET Core Runtime 10
* PostgreSQL 15
* nginx 1.18
* libpam-google-authenticator 20191231-2
* Backup appliance installation packages

In case any software updates become available for the backup appliance, these updates can be installed using the Veeam Updater service as described in section [Updating Veeam Backup for Microsoft Azure](azure_updating_vb.md).

Backup Appliance Functionality

The backup appliance performs the following administrative activities:

* Manages architecture components.
* Coordinates snapshot creation, backup and recovery tasks.
* Controls backup policy scheduling.
* Generates daily reports and email notifications.

Backup Appliance Components

The backup appliance uses the following components:

* Backup service — coordinates data protection and disaster recovery operations.

* Configuration database — stores data on the existing backup policies, worker instance configurations, connected Microsoft Azure accounts and so on, as well as information on the available and protected resources collected from Microsoft Azure.
* Configuration restore service — allows users to back up and restore the configuration database of the backup appliance.
* Web UI — provides a web interface that allows users to access the backup appliance functionality.
* Veeam Updater service — allows the backup appliance to check and install product and software package updates.

* Veeam File-Level Recovery (FLR) service — allows users to restore individual files and folders of protected Azure VMs and file shares.

* REST API service — allows users to perform operations with the backup appliance entities using HTTP requests and standard HTTP methods. For more information, see the [Veeam Backup for Microsoft Azure REST API Reference](https://helpcenter.veeam.com/references/vbazure/8.1/rest/main/tag/SectionAbout).

Page updated 2026-07-31

