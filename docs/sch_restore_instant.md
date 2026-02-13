---
title: "Performing Instant VM Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_restore_instant.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Performing Instant VM Recovery


With Instant VM Recovery, you can immediately restore Scale Computing HyperCore VMs as VMware vSphere, Microsoft Hyper-V or Nutanix AHV VMs to your production environment by running them directly from their backups. Instant VM Recovery helps you improve recovery time objectives and minimize disruption and downtime of production workloads. For more information on Instant VM Recovery, see section [VM Recovery](vm_restores.md).

|  |
| --- |
| Tip |
| It is recommended to deploy a dedicated host as a mount server and allocate a minimum of 512 MB of additional RAM for each VM disk that you want to recover at the same time. For example, if you restore a VM with 4 disks, you need an additional 2 GB of RAM on the mount server. |

To perform Instant VM Recovery, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the necessary backup job, right-click the VM you want to restore and select Instant recovery.

Alternatively, you can expand the necessary backup job, select the VM and click Instant Recovery on the ribbon.

* To restore the VM to VMware vSphere, complete the Instant Recovery wizard as described in section [Performing Instant VM Recovery of Workloads to VMware vSphere VMs](performing_instant_recovery_vm.md).
* To restore the VM to Microsoft Hyper-V, complete the Instant Recovery wizard as described in section [Performing Instant VM Recovery of Workloads to Hyper-V VMs](performing_instant_recovery_hv_vm.md).
* To restore the VM to Nutanix AHV, complete the Instant Recovery wizard as described in section [Performing Instant VM Recovery of Workloads to Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/instant_recovery_ahv.html?ver=50).

[![Instant VM Recovery](images/sch_restore_instant.webp)](images/sch_restore_instant.webp "Instant VM Recovery")


