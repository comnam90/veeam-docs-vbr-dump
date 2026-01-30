---
title: "Veeam Backup Enterprise Manager"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/enterprise_manager.html"
last_updated: "9/18/2025"
product_version: "13.0.1.1071"
---

# Veeam Backup Enterprise Manager


Veeam Backup Enterprise Manager is an optional component intended for distributed enterprise environments with multiple backup servers. Veeam Backup Enterprise Manager federates backup servers and offers a consolidated view of these servers through a web browser interface. You can centrally control and manage all jobs through a single "pane of glass", edit and clone jobs, monitor job state and get reporting data across all backup servers. Veeam Backup Enterprise Manager also enables you to search for VM guest OS files in all current and archived backups across your backup infrastructure, and restore these files in one click.

Veeam Backup Enterprise Manager Deployment

Veeam Backup Enterprise Manager can be installed on a physical or virtual machine. You can deploy it on the backup server or use a dedicated machine.

Veeam Backup Enterprise Manager Services and Components

Veeam Backup Enterprise Manager uses the following services and components:

* Veeam Backup Enterprise ManagerService coordinates all operations of Veeam Backup Enterprise Manager, aggregates data from multiple backup servers and provides control over these servers.
* Veeam Backup Enterprise Manager Configuration Database is used by Veeam Backup Enterprise Manager for storing data. The database instance can be located on PostgreSQL or Microsoft SQL Server installed either locally (on the same machine as Veeam Backup Enterprise Manager Server) or remotely.
* Veeam Guest Catalog Service replicates and consolidates VM guest OS file system indexing data from backup servers added to Veeam Backup Enterprise Manager. Index data is stored in Veeam Backup Enterprise Manager Catalog (a folder on the Veeam Backup Enterprise Manager Server) and is used to search for VM guest OS files in backups created by Veeam Backup & Replication.

Requirements for Veeam Backup Enterprise Manager

A machine where you install Veeam Backup Enterprise Manager must meet the system requirements. For more information, see the [System Requirements](https://helpcenter.veeam.com/docs/vbr/em/system_requirements.html?ver=13) section in the Enterprise Manager User Guide.

Related Topics

[Enterprise Manager Deployment on Linux](https://helpcenter.veeam.com/docs/vbr/em/em_deployment_linux.html?ver=13)


