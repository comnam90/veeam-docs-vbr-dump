---
title: "Connecting to Microsoft Entra ID Repositories (Linux Deployments)"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_manage_repo.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# Connecting to Microsoft Entra ID Repositories (Linux Deployments)

In this article

In case if your version of Veeam Backup & Replication does not have a pre-packed configuration database connection utility that allows you to connect to Entra ID repositories automatically, you need to establish the connection manually — to do that, [obtain root access](https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_remote_access.html?ver=13#managing-root-shell-access) and run the following command on the backup server:

|  |
| --- |
| VEEAM\_SETUP\_ENTRA\_ID\_PGSQL\_PASSWORD=<password> dotnet /opt/veeam/vbr/Veeam.Backup.Setup.Linux.dll entraiddbconfigurator /EntraIdSqlServerName:<servername> /EntraIdSqlServerPort:<portnumber> /EntraIdSqlServerLogin:<serverlogin> |

Make sure to run the command as a single line and specify the password, DNS name or IP address, port and login required to connect to the necessary instance.

Every time a new backup job starts, Veeam Backup & Replication will check whether a dedicated database for the protected tenant already exists on the remote PostgreSQL instance;  if there is no such database, Veeam Backup & Replication creates it. If Veeam Backup & Replication encounters any connectivity issues when running the job, you will be prompted to run a [repository rescan](entra_id_rescan_repo.md).

Page updated 12/17/2025

Page content applies to build 13.0.1.1071
