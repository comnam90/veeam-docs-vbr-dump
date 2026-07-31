---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


General

Replication has the following requirements and limitations:

* Due to VMware vSphere limitations, if you change the size of VM disks on the source VM, Veeam Backup & Replication deletes all available restore points (represented as VM snapshots) on the VM replica during the next replication job session. For more information, see [this VMware KB article](https://knowledge.broadcom.com/external/article?articleNumber=323136).
* Veeam Backup & Replication does not support the protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* * The target host must support the hardware version of the VM that you plan to replicate. For the compatibility table, see [this VMware KB article](https://knowledge.broadcom.com/external/article/312100/esxiesx-hosts-and-compatible-virtual-mac.html).
  * If you assign the role of a backup proxy to a VM, you should not add this VM to the list of processed VMs in a job that uses this backup proxy. Such configuration may result in degraded job performance. Veeam Backup & Replication will assign this backup proxy to process other VMs in the job first, and processing of this VM itself will be put on hold. Veeam Backup & Replication will report the following message in the job statistics: VM is a backup proxy, waiting for it to stop processing tasks. The job will start processing this VM only after the backup proxy deployed on the VM finishes its tasks.
  * Replication of VM templates is not supported.
  * If you use tags to categorize virtual infrastructure objects, check limitations for VM tags. For more information, see [VM Tags](vm_tags.md).
  * Due to Microsoft limitations, you cannot use Microsoft Entra ID (formerly Azure Active Directory) credentials to perform application-aware processing on VMs running Microsoft Windows 10 (or later).

* How Veeam Backup & Replication requests to assign MAC addresses to replicas depends on the MAC allocation mode configured on the vCenter Server:

* Automatic allocation. If replica is located on the same ESXi host or vCenter Server, new MAC address is assigned. If replica is located on another ESXi host or vCenter Server, MAC address is preserved.
* Manual allocation. MAC address is preserved.

* If a job is unable to complete within 21 days period, it will be stopped with the Failed status.

Re-IP, Seeding and Mapping

* You can specify static IPs or IP ranges. Do not use 0 to specify IP address ranges. In Veeam Backup & Replication, value 172.16.17.0 means a regular IP address 172.16.17.0, not an IP address range. To specify a range, use the asterisk character (\*).

The asterisk matches one entire octet, and re-IP rules match source IPs by octet only — the subnet mask is not used to select which IPs a rule applies to. For example, the source address 10.0.0.\* matches 10.0.0.0 through 10.0.0.255, but not 10.0.1.1, even if both addresses belong to the same subnet.

* Replica re-IP works only for Microsoft Windows VMs.
* Replica re-IP works only if you perform replica failover using Veeam Backup & Replication. If you power on a replica in some other way, for example, manually using a native client, re-IP rules will not be applied to it.
* The backup server OS must support mounting of the system disks of VMs that will be replicated.

* For seeding, make sure that you have backups of replicated workloads in a backup repository in the DR site. If you do not have the backups, create them as described in section [Creating Replica Seeds](replica_create_seed.md).

* Backups for seeding must be created by Veeam Backup & Replication.

* Backups for seeding must not reside in a scale-out backup repository.

Page updated 2026-05-20

