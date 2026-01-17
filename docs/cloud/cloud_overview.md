---
title: "About Veeam Cloud Connect"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html"
last_updated: "6/28/2024"
product_version: "13.0.1.1071"
---


In this article

Service providers (SP) can use Veeam Backup & Replication to offer cloud repository as a service and disaster recovery as a service to their customers (tenants). Veeam Backup & Replication lets SPs set up the cloud infrastructure so that tenants can send their data to the cloud and store it there in an easy and secure way.

SPs use their own computing, storage and network resources to configure Veeam Cloud Connect Backup and Veeam Cloud Connect Replication infrastructure components:

* Cloud repositories — storage locations in the cloud that store backups of tenant machines. Cloud repositories can be used as primary storage locations and secondary storage locations to meet the 3–2–1 backup best practice.
* Replication resources — dedicated computing, storage and network resources in the SP virtualization environment. To set up replication resources, the SP configures hardware plans and subscribes tenants to one or several hardware plans. For tenants, hardware plans appear as cloud hosts. Tenants can create VM replicas on cloud hosts and fail over to VM replicas in the cloud in case of a disaster on the production site.

Tenants who want to store their data in the cloud can connect to the SP and write their backups to cloud repositories and replicate their VMs to cloud hosts.

In This Section

* [Veeam Cloud Connect Infrastructure](cloud_infrastructure.md)
* [SP and Tenant Roles](cloud_roles.md)
* [Veeam Cloud Connect Backup](cloud_backup.md)
* [Veeam Cloud Connect Replication](cloud_replication.md)
* [Continuous Data Protection (CDP) with Veeam Cloud Connect](cloud_connect_cdp.md)
* [VMware Cloud Director Support](cloud_vcloud_director.md)
* [TLS Certificates](cloud_connect_ssl.md)
* [Tenant Lease and Quota](lease_and_quota.md)
* [Subtenants](cloud_connect_subtenants.md)
* [Data Encryption and Throttling](data_encryption_and_throttling.md)
* [Remote Connection to Tenant Backup Server](cloud_connect_remote.md)
* [Tenant Backup to Tape](cloud_connect_tape.md)
* [IPv6 Support](cloud_connect_ipv6.md)

Page updated 6/28/2024

Page content applies to build 13.0.1.1071
