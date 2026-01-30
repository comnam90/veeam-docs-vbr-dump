---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/changed_block_tracking_hv.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Changed Block Tracking


When Veeam Backup & Replication performs incremental backup, it needs to know what data blocks have changed since the previous job session. To get the list of changed data blocks, Veeam Backup & Replication uses the changed block tracking mechanism or CBT. CBT increases the speed and efficiency of incremental backups.

Veeam Backup & Replication uses CBT for the following operations:

* Backup
* Replication
* Entire VM restore

Veeam Backup & Replication enables CBT. You can disable it either at the host level or at the job level for troubleshooting purposes. Note that if you choose to run incremental jobs with CBT disabled, the backup window may increase dramatically, as Veeam Backup & Replication will read all VM data to detect what blocks have changed since the last job session.

![Changed Block Tracking](images/cbr_option_hyperv.webp)

Resilient Change Tracking

To keep track of changed data blocks, Veeam Backup & Replication uses Resilient Change Tracking or RCT. RCT is a native Microsoft Hyper-V mechanism for changed block tracking in virtual hard disks of VMs.

The RCT mechanism is used only if the Microsoft Hyper-V environment meets the following requirements:

* VMs run on Microsoft Hyper-V Server 2016 or later.
* [For Microsoft Hyper-V clusters] All hosts in the cluster are upgraded to Microsoft Hyper-V Server 2016 or later, and the cluster functional level is upgraded to 2016. If at least one node in a cluster is not upgraded to Microsoft Hyper-V Server 2016 or later, Veeam Backup & Replication does not use changed block tracking.
* VM configuration version is upgraded to 8.x.

For backup and replication with RCT, Veeam Backup & Replication uses the following mechanism:

1. Veeam Backup & Replication triggers Microsoft Hyper-V to create a checkpoint for a processed VM. The checkpoint is used as a data source for backup and replication.
2. At the end of VM processing, before a checkpoint is merged with the base VM disk, Microsoft Hyper-V converts the checkpoint to a reference point. The reference point can be thought of as a point-in-time representation of the VM disk state.
3. When Veeam Backup & Replication performs incremental backup or replication, it creates a new checkpoint for the VM used as a data source. Veeam Backup & Replication queries Microsoft Hyper-V to get incremental changes between the reference point created during the previous job session and the checkpoint created during the current job session.
4. Veeam Backup & Replication copies only changed data blocks from the created checkpoint and saves them in an incremental backup file.

To guarantee the persistence of CBT data, Microsoft RCT maintains 3 bitmaps with CBT data:

* In-memory bitmap contains the most granular CBT data.
* RCT file contains less granular CBT data than the in-memory bitmap. The RCT file is used if the CBT data in the in-memory bitmap is not available during normal operational situations, such as when a VM is moved to another host.
* MRT file has the coarsest granularity level. The MRT file is used if the CBT data in the in-memory bitmap is not available during abnormal operational situations, for example, power loss or host crash.

RCT and MRT files are created for every VM disk and stored at the VM disk level.


