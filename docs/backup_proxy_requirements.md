---
title: "Requirements and Limitations for VMware Backup Proxies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_proxy_requirements.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# Requirements and Limitations for VMware Backup Proxies


Before you assign the role of a VMware backup proxy, check the following prerequisites and limitations.

Connection to Storage

The following list shows possible connections between the machine and storage that keeps backups of this machine. The first connection is the most efficient, the last one is the least efficient.

* A machine used as a VMware backup proxy should have direct access to the storage on which VMs reside or the storage where VM data is written. This way, the VMware backup proxy will retrieve data directly from the datastore bypassing LAN.
* The VMware backup proxy can be a VM with HotAdd access to VM disks on the datastore. This type of proxy also enables LAN-free data transfer between the host and the VMware backup proxy.
* If neither of the above scenarios is possible, you can assign the role of the VMware backup proxy to a machine whose network is located closer to the source or the target storage to which the proxy will connect. In this case, VM data will be transported over LAN using the NBD protocol.

General Requirements and Limitations

* The role of a VMware backup proxy can be assigned to the following machines:

* Physical or virtual Microsoft Windows machine
* Physical or virtual Linux machine

* Before assigning the role of the VMware backup proxy to a machine, you must first add a vCenter server or ESXi host to the backup infrastructure.
* The machine must meet the system requirements. For more information, see [System Requirements](system_requirements.md#proxy).
* The account that you specify when adding a server must have permissions described in section [Permissions](required_permissions.md).

* It is recommended that you balance the number of tasks on backup proxies and backup repository to avoid the situation where some backup infrastructure resources remain idle while others are overloaded.

* You must add the machine to the Veeam Backup & Replication console as a managed server.
* Do not back up the machine used as a VMware backup proxy when it processes assigned backup or replication jobs.
* If you back up proxies that use the Virtual appliance (HotAdd) mode to process VM data, the change block tracking mechanism (CBT) will be disabled. For more information on CBT, see [Changed Block Tracking](changed_block_tracking.md).
* If you back up encrypted VMs that use the Virtual appliance (HotAdd) mode, make sure backup proxies are also encrypted. For more information, see [Encrypted VMs](encrypted_vms_backup.md).
* A VMware backup proxy should be as close to the source data as possible with a high bandwidth connection. Consider a good connection between proxy and repository.
* VMware backup proxies that use VMware VDDK-based transport modes do not support processing virtual disks with the @ symbol in the disk name.

Requirements and Limitations for VMware Backup Proxy on Linux

In addition to the general requirements and limitations, the following ones apply to Linux-based backup proxies:

* Linux-based backup proxies use the transport service for connection with backup infrastructure components. If the transport service cannot be installed, Linux-based backup proxy require SSH connection.

* You can assign the role of a VMware backup proxy to a Linux server added with single-use credentials, for example, a Linux server used as a hardened repository. For this configuration, only the Network mode (NBD) is supported, other transport modes will not be available for selection.
* Linux-based backup proxies cannot be used with VMware Cloud on AWS. This is because VDDK settings required by VMware cannot be enabled on Linux-based backup proxies.
* Linux-based backup proxies that use virtual appliance (HotAdd) transport mode do not support the VM copy scenario.
* For [Direct SAN with iSCSI access](direct_san_access.md), note that Linux-based backup proxies must have the Open-iSCSI initiator enabled.
* For [Direct NFS access](direct_nfs_access.md), consider the following:

* Linux-based backup proxies must have NFS client package installed.
* Debian-based backup proxies must have the nfs-common package installed.
* RHEL-based backup proxies must have the nfs-utils package installed.

* See recommendations for VMware backup proxy parameters in the [Veeam Backup & Replication Best Practice Guide](https://bp.veeam.com/vbr/2_Design_Structures/D_Veeam_Components/D_backup_proxies/vmware_proxies.html).


