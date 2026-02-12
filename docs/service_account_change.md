---
title: "Changing Veeam Backup & Replication Service Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/service_account_change.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Changing Veeam Backup & Replication Service Account


In some environments, you may need to run certain Veeam Backup & Replication services under a domain or local account instead of the LocalSystem account. Only specific services support changing the service account — all other Veeam Backup & Replication services must continue running under LocalSystem. The following Windows services in Veeam Backup & Replication 13 support changing the service account:

* Veeam Backup Service (VeeamBackupSvc)
* Veeam Guest Catalog Service (VeeamCatalogSvc)
* Veeam Broker Service (VeeamBrokerSvc)
* Veeam Backup Update Service (VeeamBackupUpdateSvc)
* Veeam Backup Server RESTful API Service (VeeamBackupRESTSvc)
* Veeam CDP Coordinator Service (VeeamBackupCdpSvc)
* Veeam Cloud Connect Service (VeeamCloudSvc)
* Veeam Data Analyzer Service (VeeamDataAnalyzerSvc)
* Veeam Web Service (VeeamWebSvc)

Before You Begin

Before you change the Windows service account, make sure that the new account meets all the service account and database access requirements. Check the following prerequisites:

* Ensure that the new account meets all the requirements for running Veeam Backup & Replication services, including logon rights and required local permissions. For more information on service account requirements, see [Specify Service Account Settings](install_vbr_account.md).
* Confirm that the machine where Veeam Backup & Replication runs meets all installation prerequisites, including required Windows components and features necessary for the service account. For more information on installation prerequisites, see [Before You Begin](installation_byb.md).
* Ensure that the database engine (Microsoft SQL Server or PostgreSQL) supports the authentication method required for the new service account. For more information on database selection, see [Specify Database Engine and Instance](install_vbr_sql.md).
* Verify that the new service account has the permissions it needs to work with the Veeam Backup & Replication configuration database. For more information, see Microsoft SQL and PostgreSQL sections in [Installing and Using Veeam Backup & Replication](required_permissions.md#rpvbr).
* If you use Windows authentication for the PostgreSQL configuration database, you must grant login and database access to the new service account. For more information, see [this Veeam KB article](https://www.veeam.com/kb4542).

Changing Veeam Backup & Replication Service Account

To change the Veeam Backup & Replication service account or service account password, perform the following steps for each supported service:

1. On the Veeam Backup & Replication server, open the Start menu, type services.msc, and press Enter to launch the Services console.
2. In the list of services, locate the required service (for example, Veeam Backup Service).
3. Right‑click the service and click Stop to stop the service. If the state remains Stopping, wait approximately 5 minutes for the process to complete.
4. After the service stops, right-click the service and select Properties.
5. On the Log On tab, select This account, specify the new account and password, and click Apply.
6. Click Start to start the service.
7. Repeat steps 2-6 for any other supported services that require the updated account.


