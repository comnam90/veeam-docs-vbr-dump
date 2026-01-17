---
title: "Instant Recovery"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/instant_recovery.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Instant Recovery


Authorized users can instantly recover VMs from backups to the original location or a new location included in their restore scope. Users with the Portal Administrator role have no scope limitations. For more information on restore scope, see [Configuring Restore Scope](veeam_backup_em_restore_scope.md).

Veeam Backup Enterprise Manager supports the following scenarios of Instant Recovery:

* [Instant recovery of VMware vSphere VMs to VMware vSphere](instant_recovery_vsphere.md)
* [Instant recovery of VMware Cloud Director VMs to VMware Cloud Director](instant_recovery_vcd.md)
* [Instant recovery of Microsoft Hyper-V VMs to Microsoft Hyper-V](instant_recovery_hv.md)

Using the Veeam Backup & Replication console, you can instantly recover VMware vSphere VMs to Microsoft Hyper-V and instantly recover Microsoft Hyper-V VMs to VMware vSphere. For more information, see the [VM Recovery](https://helpcenter.veeam.com/docs/vbr/userguide/vm_restores.html?ver=13) section of the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Instant Recovery is available in the Enterprise and Enterprise Plus editions of Veeam Backup & Replication. |

Supported Backup Types

You can recover workloads from the following types of backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication
* Backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication


