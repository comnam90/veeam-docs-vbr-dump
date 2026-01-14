---
title: "Connecting to a Remote Microsoft Entra ID Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_remote_repository_environment.html"
last_updated: "12/18/2025"
product_version: "13.0.1.1071"
---

# Connecting to a Remote Microsoft Entra ID Repository

In this article

A Microsoft Entra ID backup repository is a PostgreSQL instance where Veeam Backup for Microsoft Entra ID stores backups of protected Microsoft Entra ID tenants. By default, Veeam Backup & Replication saves all backed-up data to the local PostgreSQL instance installed on the backup server. To change this behavior, you can connect to a remote PostgreSQL instance and use it as the target backup repository in your Windows or Linux deployment of Veeam Backup & Replication.

|  |
| --- |
| Important |
| Due to technical limitations, Veeam Backup for Microsoft Entra ID supports connection only to one repository at a time, which means that as soon as you connect to a new repository, the connection to the previous one will be lost, and VBR will not be able to use the backups stored in the previous repository. Consider copying your existing backups from the previous PostgreSQL instance to a new one. |

In This Section

* [Connecting to Microsoft Entra ID Repositories (Windows Deployments)](entra_id_connect_remote_repo.md)
* [Connecting to Microsoft Entra ID Repositories (Linux Deployments)](entra_id_manage_repo.md)

Page updated 12/18/2025

Page content applies to build 13.0.1.1071
