---
title: "Connecting to Service Providers"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_sp.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---

# Connecting to Service Providers


The procedure of SP adding is performed by the tenant on the tenant Veeam backup server.

|  |
| --- |
| Important |
| The SP cannot add itself as a SP in the Veeam Backup & Replication console deployed on the SP backup server. |

To use Veeam Cloud Connect resources for data protection and disaster recovery tasks, you must add a SP to Veeam Backup & Replication. After you add a SP, Veeam Backup & Replication will retrieve information about backup and replication resources allocated to you, and cloud repositories and cloud hosts will become visible in your Veeam backup console. After that, you can start working with cloud resources.

Before adding a SP, [check prerequisites](cloud_connect_sp_before_you_begin.md). Then use the Service Provider wizard to add the SP.

1. [Launch the Service Provider wizard](cloud_connect_sp_launch.md).
2. [Specify cloud gateway settings](cloud_connect_sp_settings.md).
3. [Verify a TLS certificate and specify tenant account settings](cloud_connect_sp_ssl.md).
4. [Enumerate cloud repository resources](cloud_connect_sp_enumerate.md).
5. [Enumerate cloud replication resources](cloud_connect_sp_hardware_plans.md).
6. [Configure one or several network extension appliances](cloud_connect_sp_network_appliance.md).
7. [Assess results](cloud_connect_sp_apply.md).
8. [Finish working with the wizard](cloud_connect_sp_finish.md).

Related Concepts

[SP and Tenant Roles](cloud_roles.md)


