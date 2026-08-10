---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_limitations_hv.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


General

* The target host version must be equal or later than the source host version. However, you can fail back from the source 2016 host to the target 2012 R2 host if a VM replica configuration version is lower than 8.0.
* The target VM configuration version must be equal or higher than the source VM configuration version.

* [For VMs with VHD disks] If you change the size of VM disks on the source VM, Veeam Backup & Replication will delete all available restore points on the VM replica during the next replication job session.
* [For VMs with VHDX disks] If you change the size of VM disks on the source VM, Veeam Backup & Replication resets [changed block tracking (CBT)](changed_block_tracking_hv.md).
* Veeam Backup & Replication does not support the protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* Disks that were deleted from the source VM configuration are not automatically deleted from the target Hyper-V host storage.
* [Off-host replication scenario](replication_scenarios_hv.md) is possible for VMs located on a SAN storage with a hardware VSS provider and for VMs located on an SMB share with a VSS provider.
* Replication of VMs with disabled checkpoints is not supported.
* You cannot replicate VMs with shared VHDX and VHDS disks.
* Veeam Backup & Replication does not support VMs with the Trusted Launch security type on Azure Local. Backup, replication, and restore operations are not supported for this VM type.
* Azure Arc VMs are not fully supported. Backup and replication jobs may complete, but Veeam Backup & Replication cannot restore Arc VMs with Azure integration intact. Microsoft does not provide the required API for this. The restored VM is created as a standard Hyper-V VM and loses all Azure Arc management plane integration.
* Due to Microsoft limitations, you cannot use Microsoft Entra ID (formerly Azure Active Directory) credentials to perform application-aware processing on VMs running Microsoft Windows 10 (or later).
* If a job is unable to complete within 21 days period, it will be stopped with the Failed status.

Re-IP, Seeding and Mapping

* You can specify static IPs or IP ranges. Do not use 0 to specify IP address ranges. In Veeam Backup & Replication, value 172.16.17.0 means a regular IP address 172.16.17.0, not an IP address range. To specify a range, use the asterisk character (\*).

The asterisk matches one entire octet, and re-IP rules match source IPs by octet only — the subnet mask is not used to select which IPs a rule applies to. For example, the source address 10.0.0.\* matches 10.0.0.0 through 10.0.0.255, but not 10.0.1.1, even if both addresses belong to the same subnet.

* Replica re-IP works only for Microsoft Windows VMs.
* Replica re-IP works only if you perform replica failover using Veeam Backup & Replication. If you power on a replica in some other way, for example, manually using a native client, re-IP rules will not be applied to it.
* The backup server OS must support mounting of the system disks of VMs that will be replicated.

* For seeding, make sure that you have backups of replicated workloads in a backup repository in the DR site. If you do not have the backups, create them as described in section [Creating Replica Seeds](replica_create_seed_hv.md).

* Backups for seeding must be created by Veeam Backup & Replication.

* Backups for seeding must not reside in a scale-out backup repository.

Page updated 2026-05-20

