---
title: "Connecting to a Remote Microsoft Entra ID Repository"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_remote_repository_environment.html"
last_updated: "2/17/2026"
product_version: "13.0.1.1071"
---

# Connecting to a Remote Microsoft Entra ID Repository


A Microsoft Entra ID backup repository is a PostgreSQL instance where Veeam Backup for Microsoft Entra ID stores backups of protected Microsoft Entra ID tenants. By default, Veeam Backup & Replication saves all backed-up data to the local PostgreSQL instance installed on the backup server. To change this behavior, you can connect to a remote PostgreSQL instance and use it as the target backup repository in your Windows or Linux deployment of Veeam Backup & Replication. Consider that Veeam Backup for Microsoft Entra ID supports only [PostgreSQL password authentication](https://www.postgresql.org/docs/current/auth-password.html) to connect to remote Microsoft Entra ID backup repositories.

|  |
| --- |
| Important |
| Due to technical limitations, Veeam Backup for Microsoft Entra ID supports connection only to one repository at a time, which means that as soon as you connect to a new repository, the connection to the previous one will be lost, and VBR will not be able to use the backups stored in the previous repository. Consider copying your existing backups from the previous PostgreSQL instance to a new one. |

In This Section

* [Connecting to Microsoft Entra ID Repositories (Windows Deployments)](entra_id_connect_remote_repo.md)
* [Connecting to Microsoft Entra ID Repositories (Linux Deployments)](entra_id_manage_repo.md)


