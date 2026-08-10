---
title: "Backup Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_appliances.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Appliances


A backup appliance is a Linux-based EC2 instance that is used to manage solution architecture components, perform data protection and disaster recovery operations with AWS resources, and generate daily reports and email notifications.

The backup appliance uses the following services:

* Backup service — coordinates data protection and disaster recovery operations.

* Configuration restore service — allows users to back up and restore the configuration of the backup appliance.
* Veeam Updater service — allows the backup appliance to check, view and install product and software package updates.
* Veeam FLR service — allows users to restore individual files and folders of protected EC2 instances.
* Self Backup service — allows the backup appliance to back up and restore the configuration database of the backup appliance.
* REST API service — allows users to perform operations with the backup appliance entities using HTTP requests and standard HTTP methods. For more information, see the [Veeam Plug-in for AWS](https://helpcenter.veeam.com/references/vbaws/10/rest/1.8-rev0/tag/SectionOverview) [REST API Reference](https://helpcenter.veeam.com/references/vbaws/11/rest/1.9-rev0/tag/SectionOverview).
* Configuration database — stores data on the existing backup policies, worker instance configurations, added IAM roles, sessions and so on, as well as information on the available and protected resources collected from AWS.
* Web UI — provides a web interface that allows users to access the backup appliance functionality.

|  |
| --- |
| Tip |
| If you have multiple backup appliances, you can add these appliances to Veeam Backup & Replication, and then use the [Veeam Backup & Replication console](https://helpcenter.veeam.com/docs/vbr/userguide/backup_console.html?ver=13) as the central management console for backup appliance operations. |

Backup Appliance Software

The backup appliance comes with the pre-installed set of software components:

* Ubuntu 22.04 LTS
* ASP.NET Core Runtime 10.0.10
* PostgreSQL 15
* nginx 1.18
* libpam-google-authenticator 20191231-2
* Backup appliance installation packages

In case any software updates become available for the backup appliance, these updates can be installed using the Veeam Updater service as described in section [Upgrade and Update](aws_update_vb.md).

Page updated 2026-08-03

