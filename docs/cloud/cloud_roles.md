---
title: "SP and Tenant Roles"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_roles.html"
last_updated: "12/15/2025"
product_version: "13.0.1.1071"
---


In this article

Communication in the cloud is carried out between two parties: SP on one side and tenants on the other side.

* The SP is an organization that provides cloud services to tenants:

+ Backup as a Service (Veeam Cloud Connect Backup)
+ Disaster Recovery as a Service (Veeam Cloud Connect Replication)

* The tenant is an SP customer who wants to copy data offsite, store backups in a cloud repository or create VM replicas on a cloud host on the SP side.

|  |
| --- |
| Note |
| Veeam Cloud Connect does not support Role-Based Access Control (RBAC). Tenants cannot be assigned custom roles to control access to the SP cloud infrastructure. |

SP Tasks

In the cloud, the SP is responsible for performing the following tasks:

Veeam Cloud Connect Backup Tasks

* Configuring the Veeam Cloud Connect Backup infrastructure — environment needed to expose cloud repository resources to tenants. As part of this process, the SP takes the following steps:

+ Decides what backup repositories must be used as cloud repositories.
+ Sets up TLS certificates to enable secure communication in the Veeam Cloud Connect infrastructure.
+ Configures cloud gateways.
+ Registers tenant accounts.

* Managing tenant accounts and tenant data to ensure flawless work of the Veeam Cloud Connect infrastructure.
* Performing selected data recovery operations from tenant backups.

Veeam Cloud Connect Replication Tasks

* Configuring the Veeam Cloud Connect Replication infrastructure — environment needed to expose SP virtualization resources as cloud hosts to tenants. As part of this process, the SP takes the following steps:

+ Sets up TLS certificates to enable secure communication in the Veeam Cloud Connect infrastructure.
+ Configures cloud gateways.
+ Allocates VLANs for cloud networking.
+ Allocates public IP addresses for tenant VM replicas.
+ Configures hardware plans or VMware Cloud Director resources to provide tenants with computing, storage and network resources to create VM replicas in the cloud and perform failover tasks with VM replicas on the cloud host.
+ Registers tenant accounts.

* Managing tenant accounts and tenant data to ensure flawless work of the Veeam Cloud Connect infrastructure.
* Running tenant cloud failover plans to perform full site failover and managing tenant VM replicas upon tenant requests.

Tenant Tasks

Tenants, on their hand, are responsible for performing the following tasks:

* Connecting to the SP to be able to use Veeam Cloud Connect resources (cloud repository and cloud host).
* Configuring and running backup and backup copy jobs targeted at cloud repositories.
* Configuring and running replication jobs and CDP policies targeted at cloud hosts.
* Performing restore tasks with VM backups created by backup jobs.
* Configuring cloud failover plans to perform full site failover for VM replicas.
* Performing failover tasks with VM replicas created by replication jobs and CDP policies.
* Configuring subtenant accounts to allow tenant-side users to create Veeam Agent backups in a cloud repository. To learn more, see [Subtenants](cloud_connect_subtenants.md).
* Performing restore tasks with Veeam Agent backups created by subtenants in a cloud repository.

|  |
| --- |
| Note |
| Consider the following:   * A set of tasks available to the tenant depends on the type of the tenant account. To learn more, see [Tenant Account Types](cloud_tenant_types.md). * It is recommended that the tenant enables the encryption option for backup jobs targeted at the cloud repository. Data encryption helps tenants protect sensitive VM data from unauthorized access while this data is stored in the cloud repository.   On the SP side, the SP should ensure integrity of tenant backups. It is not recommended that the SP uses tenant backups to perform operations that go beyond the scope of regular Veeam Cloud Connect tasks. For example, importing a tenant backup in the Veeam Backup & Replication console on the SP backup server and performing recovery verification of this backup with a SureBackup job may result in failure of the tenant backup job and corruption of the configuration database on the SP backup server. |

SP and Tenant Roles in Managed Service Scenario

In addition to Backup as a Service (Veeam Cloud Connect Backup) and Disaster Recovery as a Service (Veeam Cloud Connect Replication), the SP can use Veeam Backup & Replication to offer the Managed Service (MSP Backup and Disaster Recovery as a Service) to tenants. In this scenario, the tenant may not take part in deploying and managing backup infrastructure. The SP takes responsibility for configuring backup infrastructure on the tenant side and performing all data protection and disaster recovery tasks. To learn more, see [Managed Service (MSP Backup)](cloud_connect_licensing.md#baas).

Page updated 12/15/2025

Page content applies to build 13.0.1.1071
