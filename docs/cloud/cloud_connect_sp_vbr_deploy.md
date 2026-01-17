---
title: "Deploying SP Veeam Backup Server"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_sp_vbr_deploy.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Deploying SP Veeam Backup Server


To deploy the SP Veeam backup server, you must install Veeam Backup & Replication on a Microsoft Windows server on the SP side.

The installation process of Veeam Backup & Replication in the Veeam Cloud Connect infrastructure is the same as the installation process in a regular Veeam backup infrastructure. To learn more about system requirements, required permissions and the installation process workflow, see the [Deployment](https://helpcenter.veeam.com/docs/vbr/userguide/deployment.html?ver=13) section in the Veeam Backup & Replication User Guide.

In addition to requirements listed in the product documentation, the SP Veeam backup server must meet the following requirements:

1. On the SP Veeam backup server, a Veeam Cloud Connect license must be installed. Other types of licenses do not support the Veeam Cloud Connect functionality.
2. The SP Veeam backup server must have access to all components of the Veeam Cloud Connect infrastructure deployed on the SP side. These include:

* Backup repositories that will be used as cloud repositories
* Managed servers that will be used for configuring replication resources (cloud hosts)
* Cloud gateways
* [Optional] Target WAN accelerators

1. If the SP plans to use Veeam Backup for Microsoft 365 to provide Mail Backup as a Service to tenants, the SP must install Veeam Backup for Microsoft 365 on the SP backup server. For further information, see the [For Service Providers](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_baas_sp.html?ver=80 ) section of the Veeam Backup for Microsoft 365 User Guide.

|  |
| --- |
| Important |
| It is recommended that the SP regularly creates encrypted backups of the SP Veeam backup server configuration database. With the encryption option enabled, Veeam Backup & Replication will include in the configuration backup passwords for tenant accounts created on the SP backup server. As a result, if the configuration data becomes corrupted for some reason, after configuration restore, the SP will not have to specify new passwords for registered tenant accounts.  To learn more, see the [Creating Encrypted Configuration Backups](https://helpcenter.veeam.com/docs/vbr/userguide/config_backup_encrypted.html?ver=13) section in Veeam Backup & Replication User Guide. |


