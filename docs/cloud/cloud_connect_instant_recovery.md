---
title: "Instant Recovery from Tenant Backups"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_instant_recovery.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can perform Instant Recovery for tenant workloads, that is, recover workloads from tenant backups in the cloud repository and register them as VMs on a VMware vSphere host on the SP side. This may be helpful in case a machine on the tenant side becomes unavailable, and the tenant cannot fail over to a VM replica on the cloud host. Instead, the tenant can request the SP to recover the necessary VM from the backup.

To use this functionality, the SP and tenant must make sure that the following conditions are met:

* To allow the SP to view tenant backups in the SP backup console, the tenant must select the Allow this Veeam Backup & Replication installation to be managed by the service provider check box when connecting to the SP. For details, see [Connecting to Service Providers](cloud_connect_sp.md).

|  |
| --- |
| Note |
| For Veeam Agent users, consider that to display on the SP side backups created by Veeam Agent in the standalone mode, a backup server connected to the SP with the Allow this Veeam Backup & Replication installation to be managed by the service provider option enabled is required. |

* The target VMware vSphere host where the SP plans to register the recovered VMs must be added to the Veeam Backup & Replication infrastructure on the SP backup server.
* Veeam Cloud Connect supports Instant Recovery from unencrypted backups only.

Instant Recovery from tenant backups works in the similar way as the regular one. For more information, see the [Instant Recovery to VMware vSphere](https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery.html?ver=13) section in the Veeam Backup & Replication User Guide.

Considerations and Limitations

For Instant Recovery from tenant backups, consider the following:

* Veeam Cloud Connect supports Instant Recovery from any type of tenant backups for which recovery to VMware vSphere is supported. This includes VM backups, Veeam Agent backups and backups created by backup copy jobs in the cloud repository.

Note that Veeam Cloud Connect supports Instant Recovery to VMware vSphere only. Other platforms are not supported as an Instant Recovery target.

* Veeam Cloud Connect supports Instant Recovery from backups that reside in the performance tier, capacity tier or archive tier.
* During Instant Recovery, the tenant account will be in the disabled state.

[For backups in the archive tier] The Instant Recovery operation will be pending until the backed-up data is retrieved from the archive tier. Data retrieval time may take from several minutes to several hours depending on the object storage system and data retrieval method. During this time, the tenant account will be in the disabled state. For more information on data retrieval cost and speed, see the [Data Retrieval](https://helpcenter.veeam.com/docs/vbr/userguide/archive_tier_retrieval.html?ver=13) section in the Veeam Backup & Replication User Guide.

Note that after Instant Recovery, the tenant account remains in the disabled state. The SP needs to manually enable the tenant account. For details, see [Disabling and Enabling Tenant Accounts](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_disable_account.html?ver=120).

* Migration of a recovered VM back to the tenant production site is unavailable. The SP can finalize the Instant Recovery process by migrating the VM to the SP virtual environment.
* Separate prerequisites and limitations apply to Instant Recovery from VM backups and Instant Recovery from Veeam Agent backups. For details, see the following sections in the Veeam Backup & Replication documentation:

* For Instant Recovery from VM backups, see the [Considerations and Limitations](https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_before_you_begin_vm.html?ver=13) section in the Veeam Backup & Replication User Guide.
* For Instant Recovery from Veeam Agent backups, see the [Restoring Veeam Agent Backup to vSphere VM](https://helpcenter.veeam.com/docs/vbr/userguide/integration_instant_restore_vsphere.html?ver=13) section in the Veeam Backup & Replication User Guide.

Tenant Backups in SP Backup Console

In the SP Veeam backup console, tenant backups are displayed under the Backups node of the Home view. To identify tenant backups available for Instant Recovery, as well as the owner of the backup, the SP can use the Tenant Name column in the working area:

* For VM backups and Veeam Agent backups created under the tenant account, Veeam Backup & Replication displays the tenant account name in the Tenant Name column.
* For Veeam Agent backups created under the subtenant account, Veeam Backup & Replication displays the subtenant account name in the Tenant Name column.

Related Tasks

[Performing Instant Recovery from Tenant Backups](cc_perform_instant_recovery.md)

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
