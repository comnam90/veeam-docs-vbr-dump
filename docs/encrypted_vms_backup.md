---
title: "Encrypted VMs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encrypted_vms_backup.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# Encrypted VMs


|  |
| --- |
| Note |
| All limitations and considerations below also apply to a VM with a Virtual Trusted Platform Module (vTPM) as vTPM requires VM encryption to be enabled. |

Veeam Backup & Replication provides support for VMware vSphere encrypted VMs.

* [Backup of encrypted VMs](#backup)
* [Restore of encrypted VMs](#restore)
* [Replication of encrypted VMs](#replication)
* [Failback of encrypted VM replicas](#failback)

|  |
| --- |
| Note |
| CDP meets specific requirements for VMs encrypted on VMware side. For more information, see the [Virtual Machines](cdp_requirements.md#vm) section. |

Backup of Encrypted VMs

To back up VMware encrypted VMs, the backup infrastructure must meet the following requirements:

* VM encryption instances must be preconfigured in the virtual infrastructure: you must set up the Key Management Server (KMS), create the VM encryption policy, and assign it to VMs in advance.
* The backup proxy must be working in the Virtual appliance or Network transport mode:

+ The backup proxy working in the Virtual appliance transport mode must be deployed on an encrypted VM.
+ The backup proxy working in the Network transport mode uses the NBD protocol by default. If you want to use NBDSSL, select the Enable host to proxy traffic encryption in Network mode (NBDSSL) check box in the Transport Mode window. Note that traffic encryption puts more stress on the CPU of an ESXi host and can decrease performance.

Restore of Encrypted VMs

Veeam Backup & Replication supports the following restore options:

* Restore encrypted VM as encrypted or unencrypted.
* Restore unencrypted VM as encrypted.

The backup infrastructure must meet the following requirements:

* VM encryption instances must be preconfigured in the virtual infrastructure: you must set up the Key Management Server (KMS), create the VM encryption storage policy, and assign it to VMs in advance.

* The backup proxy must be working in the Virtual appliance or Network transport mode:

+ The backup proxy working in the Virtual appliance transport mode must be deployed on an encrypted VM.
+ The backup proxy working in the Network transport mode uses the NBD protocol by default. If you want to use NBDSSL, select the Enable host to proxy traffic encryption in Network mode (NBDSSL) check box in the Transport Mode window. Note that traffic encryption puts more stress on the CPU of an ESXi host and can decrease performance.

If you restore a VM as an encrypted one to the specified location, ensure that the target datastore is under the VM Encryption Policy node.

If a VM has several disks, you can optionally restore some disks as encrypted and some disks as unencrypted. Keep in mind, that even if one disk is restored as encrypted, the VM configuration file must also be placed on a datastore under the VM Encryption Policy node.

Replication of Encrypted VMs

To replicate VMware encrypted VMs, the backup infrastructure must meet the following requirements:

* VM encryption instances must be preconfigured in the virtual infrastructure: you must set up the Key Management Server (KMS), create the VM encryption policy, and assign it to VMs in advance. Ensure that you use a common KMS or the KMS clusters at both sites use common encryption keys.

|  |
| --- |
| Note |
| If you do not set up KMS, the replication job will not fail, but replicated VMs will not be encrypted in this case. |

* Source and target backup proxies must be working in the Virtual appliance or Network transport mode:

+ The backup proxy working in the Virtual appliance transport mode must be deployed on an encrypted VM.

+ The backup proxy working in the Network transport mode uses the NBD protocol by default. If you want to use NBDSSL, select the Enable host to proxy traffic encryption in Network mode (NBDSSL) check box in the Transport Mode window. Note that traffic encryption puts more stress on the CPU of an ESXi host and can decrease performance.

To replicate a VM as an encrypted one, place disks and the configuration file of the VM replica on datastores compatible with the VM encryption policy:

1. At the Destination step of the wizard, click Choose near the Datastore field.
2. In the Select Datastore window, select a datastore under the VM Encryption Policy node.

|  |
| --- |
| Note |
| Guest OS file restore for encrypted VM replicas is not supported. |

Failback of Encrypted VM Replicas

To fail back VMware encrypted VMs replicas, the backup infrastructure must meet the following requirements:

* VM encryption instances must be preconfigured in the virtual infrastructure: you must set up the Key Management Server (KMS), create the VM encryption policy and assign it to VMs in advance. Ensure that you use a common KMS or the KMS clusters at both sites use common encryption keys.

* Source and target backup proxies must be working in the Virtual appliance or Network transport mode:

+ The backup proxy working in the Virtual appliance transport mode must be deployed on an encrypted VM.

+ The backup proxy working in the Network transport mode uses the NBD protocol by default. If you want to use NBDSSL, select the Enable host to proxy traffic encryption in Network mode (NBDSSL) check box in the Transport Mode window. Note that traffic encryption puts more stress on the CPU of an ESXi host and can decrease performance.

If you fail back an encrypted VM replica to the specified location, ensure that the target datastore is under the VM Encryption Policy node.


