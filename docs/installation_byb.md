---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/installation_byb.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you install Veeam Backup & Replication, check the following prerequisites:

* A machine on which you plan to install Veeam Backup & Replication must meet the system requirements. For more information, see [System Requirements](system_requirements.md).
* We do not recommend you to install Veeam Backup & Replication directly on a Hyper-V host. Such installation may lead to unpredictable system behavior. Instead, create a VM on the host and install Veeam Backup & Replication on the VM.

* A user account that you plan to use for installation must have sufficient permissions. For more information, see [Permissions](required_permissions.md).
* Backup infrastructure components communicate with each other over specific ports. These ports must be open. For more information, see [Ports](used_ports.md).

* You must remove Veeam Backup & Replication components of versions that are not supported by the upgrade procedure from the target machine. You may also need to remove earlier versions of other Veeam products and components.
* Before deploying Veeam Backup & Replication, define where the Veeam Backup & Replication server will be located. Depending on what kind of protection are you planning to use, the Veeam Backup & Replication server should be located on the source site or the Disaster Recovery site.

* When replication or CDP is used: If you plan to use [replication](replication.md) or [Continuous Data Protection](cdp_replication.md) (CDP), the Veeam Backup & Replication server should be deployed in the disaster recovery site. In case of source side failures, Veeam Backup & Replication will be available for failover operations. The source backup infrastructure can be managed with the same Veeam Backup & Replication server with the help of backup proxies deployed on the source site.
* When only backup features are used: If you plan to use Veeam Backup & Replication for backup jobs only, the backup server should be placed in the production site.

* We strongly recommend that no highly-transactional and business-critical software is deployed on the same machine as the Veeam backup server. This could be (but not limited to) software such as Active Directory, Exchange Server or other intensive production databases on the SQL server instance. We recommend that only Veeam Backup & Replication runs on the backup server.

Configuration Database

Before deploying Veeam Backup & Replication, decide which database engine and version you need to use:

* If you do not prepare a database engine in advance, Veeam Backup & Replication will automatically install PostgreSQL locally on the backup server.
* Decide if you need the database engine installed on the same server as Veeam Backup & Replication or on a remote server. Veeam Backup & Replication requires a database engine deployed either locally on the backup server or remotely.

It is recommended to run the database engine instance locally to eliminate latency issues. However, in some scenarios a remote instance can be the better choice:

* High Availability. SQL Clustering and Always On Availability Group on external SQL Servers can be used for high availability of the configuration database. To learn about the configuration details, see [this Veeam KB article](https://www.veeam.com/kb2301).
* Licensing. Some enterprises have dedicated virtual clusters for SQL Servers due to licensing constraints. In such cases, you can place the Veeam configuration database on an existing instance to lower the total cost of ownership.

* If you prefer to use an Express Edition of Microsoft SQL Server as your database engine, note that its usage is limited by 10 GB of configuration database. The Express Edition is enough for evaluation purposes and not very large environments (<500 VMs). If your infrastructure is large (more than 500 VMs), you may consider to install a Microsoft SQL Server in advance.
* If Microsoft SQL Server is installed by the previous product version, Veeam Backup & Replication will connect to the existing configuration database, upgrade it (if necessary) and use it for work.

* If you already have an installed instance of PostgreSQL and want to use it for the configuration database, ensure that the LocalSystem account is added to your PostgreSQL configuration to successfully run the installation of Veeam Backup & Replication.

Configuring PostgreSQL Instance

The default PostgreSQL instance is configured to consume a minimum amount of resources, which may not be enough for Veeam Backup & Replication performance.

When installing Veeam Backup & Replication, you can choose what PostgreSQL instance to use for the Veeam Backup & Replication configuration database. You can use an already installed PostgreSQL instance or install a new one.

* If you let the setup install a new PostgreSQL instance, it will be configured automatically.
* If you want to use an already installed PostgreSQL instance, make sure that the instance configuration is sufficient for the Veeam Backup & Replication performance.

To adjust the configuration of an existing PostgreSQL instance, see [Adjusting PostgreSQL Instance Configuration](postgresql_instance_configuration.md).

Related Topics

[Planning and Preparation](planning.md)


