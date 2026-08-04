---
title: "Restoring Data from Tenant Backups"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_data_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Data from Tenant Backups


The SP can restore data from tenant backups that reside in the cloud repository. To use this functionality, the SP must have access to tenant backups on the SP side.

* For standalone tenant accounts, tenant backups are available on the SP side if the tenant selected the Allow this Veeam Backup & Replication installation to be managed by the service provider check box when connecting to the SP. For details, see [Connecting to Service Providers](cloud_connect_sp.md).

* For data restore from backups created by Veeam Agent in the standalone mode, a tenant backup server connected to the SP with the Allow this Veeam Backup & Replication installation to be managed by the service provider option enabled is required.

|  |
| --- |
| Note |
| By default, the SP Veeam Backup & Replication console does not display encrypted tenant backups. The SP can restore encrypted tenant backups only if the tenant grants the SP restore access to all backups. For details, see [Access to Tenant Backups](cc_sp_restore_access.md). |

The set of data restore operations available on the SP side differs from the one on the tenant side. The SP can perform the following tasks:

* [Performing Entire VM Restore from Tenant Backups](cloud_connect_vm_restore_sp.md):

* Restoring to Nutanix AHV
* Restoring to Proxmox VE
* Restoring to oVirt KVM
* Restoring to Scale Computing HyperCore
* Restoring to HPE Morpheus VM Essentials

* [Restoring to Amazon EC2](cc_restore_aws.md)
* [Restoring to Microsoft Azure](cc_restore_azure.md)

* [Performing Instant Recovery from Tenant Backups](cc_perform_instant_recovery.md)

* [Disk restore](cc_disk_restore.md) (using Veeam PowerShell cmdlets only)
* [Disk publishing](cc_disk_publish.md) (using Veeam PowerShell cmdlets only)

Page updated 2026-07-29

