---
title: "Enterprise Manager Components"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_components.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager incorporates the following services and components:

* Veeam Backup Enterprise Manager Service coordinates all operations performed by Veeam Backup Enterprise Manager such as backup, replication, recovery verification and restore tasks. On Microsoft Windows machines, the service runs under the Local System account or an account that has the Local Administrator permissions on the backup server. This service is installed and started automatically on the local Windows server.
* Veeam Enterprise Manager Identity Service manages authentication and identity-related operations for Veeam Backup Enterprise Manager.
* Veeam Catalog Service is used for guest OS file indexing, index data retention and its synchronization with the information on backup servers. It comprises a Windows service named Veeam Guest Catalog also installed on the Veeam Backup Enterprise Manager server. For more information, see [Veeam Backup Catalog](veeam_backup_catalog.md).
* Veeam Enterprise Manager Web UI Service hosts and delivers the Veeam Backup Enterprise Manager web application when deployed on Linux-based systems.

* Veeam Backup Enterprise Manager REST API Service allows you to communicate with Veeam Backup Enterprise Manager using HTTP and HTTPS protocols and the principles of REST. For more information, see the [Veeam Backup Enterprise Manager REST API Reference](https://helpcenter.veeam.com/docs/vbr/em_rest/overview.html?ver=13).

* [For Linux-based Enterprise Manager] Veeam Updater and Veeam Updater package manager are used to manage Veeam Software Appliance updates, this includes OS and Enterprise Manager updates. For details, see [Veeam Software Appliance Update](em_update_linux.md).
* [For Linux-based Enterprise Manager] Veeam Host Management Service allows you to configure host settings. For details, see [Host Management](em_vhm.md).

* Veeam Plug-in for VMware vSphere Client Service allows vSphere administrators to manage backup infrastructure of the virtual environment. For more information, see [Veeam Plug-in for VMware vSphere Client](vsphere_plugin.md).

* [For Microsoft Windows-based Enterprise Manager] VeeamBackup and VeeamBackup site (IIS extension) application pools are created and displayed in IIS Manager. These web applications are deployed on the local IIS web server.

* Web interfaces used to access Veeam Backup Enterprise Manager from different infrastructures:

* Main web interface is used to browse and perform operations with jobs, backups and machines, to configure Enterprise Manager functionality and control infrastructure. For more information, see [Exploring Enterprise Manager](em_know_ui.md).
* Veeam Self-Service File Restore Portal that allows administrators to restore files or folders from the guest OS of a virtual or physical machine. For more information, see [Using Self-Service File Restore Portal to Restore Machine Guest Files](em_self_restore.md).
* Veeam Self-Service Backup Portal and Veeam Plug-in for VMware Cloud Director that provide members of VMware Cloud Director organizations with a UI for self-service operations on machine protection. For more information, see [Veeam Self-Service Backup Portal for Cloud Director](em_working_with_vcd_vms.md).
* VMware vSphere Self-Service Backup Portal that provides Service Providers with a UI for managing access permissions and vSphere quotas for their customers. For more information, see [vSphere Self-Service Backup Portal](em_working_with_vsphere_portal.md).

|  |
| --- |
| Note |
| Veeam Self-Service File Restore Portal, Veeam Self-Service Backup Portal, Veeam Plug-in for VMware Cloud Director and VMware vSphere Self-Service Backup Portal features are available in the Enterprise Plus edition license. |

* PostgreSQL or Microsoft SQL Server database is used to store configuration and performance data. Note that you can use a Microsoft SQL Server database with Microsoft Windows-based Enterprise Manager only.

* Veeam Backup Search is an optional component used for guest OS file indexing of protected machines. This component is included in the installation package to provide backward compatibility with older existing deployments. For a new deployment, there is no need to install Veeam Backup Search since all operations related to guest OS file indexing and search will be performed by Veeam proprietary built-in indexing engine. For more information, see [Veeam Backup Search Capabilities](understanding_search.md).

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
