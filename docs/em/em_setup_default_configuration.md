---
title: "em_setup_default_configuration"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_setup_default_configuration.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---


In this article

At the Ready to Install step of the wizard, you can select to install Veeam Backup Enterprise Manager with default installation settings or specify custom installation settings.

* To use the default installation settings, click Install.
* To use custom installation settings, click Customize Settings. The setup wizard will include additional steps that will let you configure installation settings.

The table below lists the default installation settings.

| Setting | Default Value | Description |
| --- | --- | --- |
| Installation folder | %ProgramFiles%\Veeam\Backup and Replication | Folder where Veeam Backup Enterprise Manager is installed. |
| Guest catalog folder | C:\VBRCatalog | The VBRCatalog folder on a volume with the maximum amount of free space.  The guest catalog folder stores indexing data for VM guest OS files. Indexing data is required for browsing and searching for VM guest OS files inside backups and performing 1-click restore. |
| Service account | LOCAL SYSTEM | Account under which the Veeam Backup Enterprise Manager runs. |
| Database engine | PostgreSQL | The setup installs PostgreSQL locally on the Veeam Backup Enterprise Manager server. |
| Database name | VeeamBackupReporting | The setup deploys the Veeam Backup Enterprise Manager configuration database on the locally installed instance of PostgreSQL. |
| Catalog service port | 9393 | The catalog service port is used by the Veeam Guest Catalog Service to replicate catalog data from backup servers to Veeam Backup Enterprise Manager. |
| Service port | 9394 | The service port is used by Veeam Backup Enterprise Manager to collect data from backup servers. |
| Web UI ports | For HTTP protocol: 9080  For HTTPS protocol: 443 | These ports are used for accessing Veeam Backup Enterprise Manager web interface. |
| REST API service ports | For HTTP protocol: 9399  For HTTPS protocol: 9398 | These ports are used for accessing Veeam Backup Enterprise Manager REST API. |
| Certificate | Self-signed certificate will be generated automatically | During installation a self-signed certificate is generated that will be used for all Enterprise Manager connections. You can update the certificate upon installation. For more information, see [Managing TLS Certificates](tls_certificates.md). |
| Check for updates | Automatically | Veeam Backup Enterprise Manager will check for product updates weekly. When a new product build is published on the Veeam update server, a notification is displayed in the Windows Action Center. |

![Step 6. Review Default Installation Settings](images/em_setup_default_cfg.webp "Default Installation Settings")

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
