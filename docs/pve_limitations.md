---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_limitations.html"
last_updated: "2/17/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for Proxmox VE, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for Proxmox VE, consider the following:

* Veeam Plug-in for Proxmox VE supports Proxmox Virtual Environment deployments created using the official ISO image provided by Proxmox only.
* Veeam Plug-in for Proxmox VE supports only the /bin/bash shell to perform management operations with the Proxmox VE server.
* Veeam Plug-in for Proxmox VE supports custom certificates installed on the Proxmox VE server if either of the following conditions is met:

* The full certificate chain has been uploaded to the Proxmox VE server.
* The backup infrastructure components, such as workers, are able to connect to the CA server and validate the certificate.

* Veeam Plug-in for Proxmox VE does not support Online Certificate Status Protocol (OCSP) certificates to access the Proxmox VE server.
* Veeam Plug-in for Proxmox VE does not support Proxmox Virtual Environment deployments with S3 buckets connected as storage.
* Veeam Plug-in for Proxmox VE does not support credentials of the [SSH Private Keys type](credentials_manager_linux_pubkey.md) to access the Proxmox VE server.
* Veeam Plug-in for Proxmox VE does not support user accounts with multi-factor authentication to access the Proxmox VE server.

* Veeam Plug-in for Proxmox VE does not support the IPv6 protocol.

* The Proxmox VE server must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

* Before you [add a Proxmox VE server](pve_sever_add.md) to the backup infrastructure, ensure that it has been assigned a unique Proxmox VE system UUID and its name does not contain an FQDN.

* If you want to protect VMs that reside in a Proxmox VE cluster, all nodes of these cluster must be added to the backup infrastructure separately. Adding clusters as standalone entities is not supported.
* After you add nodes of a cluster to the backup infrastructure, you must not change the name of the cluster in the Proxmox VE administration portal.
* After you make changes to your Proxmox VE environment (for example, you migrate a VM between cluster nodes), these changes may not appear in Veeam Backup & Replication immediately — the data synchronization process between the backup server and the Proxmox VE server may take up to 15 minutes to complete. You can speed up the data synchronization process by [rescanning the Proxmox VE server](pve_server_rescan.md).

Backup Repositories

When managing backup repositories, consider that Veeam Plug-in for Proxmox VE does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) and [HPE Cloud Bank Storage](storeonce_supported_features.md) repositories. However, you can use them for [storing copies of backups](pve_backups_copy.md) created with Veeam Plug-in for Proxmox VE.

Workers

When configuring workers, consider the following:

* The default local storage must be enabled on all hosts where worker VMs will be deployed. If you cannot use the default storage in your environment, contact [Veeam Customer Support](pve_export_logs.md).
* The storage where system files of workers will be stored must [support snapshots](https://pve.proxmox.com/wiki/Storage).
* For VLAN-tagged environments, the VLAN ID must be manually assigned to worker VMs after they are deployed or redeployed.
* When transferring VM data to and from backup repositories, workers rely on the Hot-Add and NBD transport modes.

Backup

When protecting Proxmox VE resources, consider the following:

* Veeam Plug-in for Proxmox VE does not support backup of LXC containers.

* Veeam Plug-in for Proxmox VE does not support backup of VM templates.
* Veeam Plug-in for Proxmox VE does not support backup of VMs created from [templates as linked clones](https://pve.proxmox.com/wiki/VM_Templates_and_Clones#Linked_Clone). Backup of full clones is supported.
* Veeam Plug-in for Proxmox VE does not support backup of VMs with the same BIOS UUID.

* Veeam Plug-in for Proxmox VE does not support backup of iSCSI disks. If iSCSI disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Proxmox VE does not support backup of directly attached (passthrough) disks. If such disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Proxmox VE does not support backup of VM permissions granted to users, user groups and API tokens.

* Veeam Plug-in for Proxmox VE does not support backup of VMs that store their disks in the BTRFS and custom storage. All other [Proxmox VE storage types](https://pve.proxmox.com/wiki/Storage) are supported.
* The number of concurrent backup operations performed in each storage is limited to 4 to avoid excessive load on the production environment. To change the limit, contact [Veeam Customer Support](pve_export_logs.md).

* Veeam Plug-in for Proxmox VE does not support VM replication.

Guest Processing

When configuring guest processing in backup jobs, consider the following:

* The file exclusion functionality is not supported.

* Veeam Plug-in for Proxmox VE cannot [use Kerberos authentication](https://helpcenter.veeam.com/docs/vbr/userguide/kerberos_authentication.html?ver=13) while connecting to guest OSes of the processed VMs.

* When restoring a database using Veeam Explorers to the original VM, the VM hostname is used instead of the FQDN name. If Veeam Explorers cannot reach the VM, you can add the FQDN name and the IP address of the VM to the hosts file on the backup server.
* If you import backups created by a job with guest processing enabled, this backup job will truncate transaction logs but it will not store transaction log backups in the repository. To avoid the issue, before running the job, either clone the job and perform active full, or contact contact Veeam Customer Support.
* Image-level, application-aware backups of Veeam Backup for Microsoft 365 servers running on Proxmox VE clusters are not Veeam Microsoft 365 restore explorers-aware. The behavior described in [this article](https://bp.veeam.com/vb365/guide/design/vb365_with_vbr) is currently unsupported for Proxmox VE backups.

* Veeam Plug-in for Proxmox VE will not be able to create an application-consistent backup of a Microsoft SQL Server running a Windows Server Failover Cluster. If you add such a VM to the backup job scope and enable application-aware processing for it, Veeam Backup & Replication will only create an image-level backup. To work around the limitation, [use Veeam Agent](agents_cluster_support.md) managed by Veeam Backup & Replication instead.

Restore

When restoring Proxmox VE resources, consider the following:

* Starting from version 9, Proxmox VE supports the [snapshot-as-volume-chain](https://pve.proxmox.com/wiki/Storage%3A_LVM) functionality for some storage types. Since this functionality is available for VMs using QEMU version 10 and later, Veeam Plug-in for Proxmox VE is not able to restore VMs using an earlier QEMU version to a storage with the Allow Snapshots as Volume-Chain setting enabled. To work around the issue, see [this Veeam KB article](https://www.veeam.com/kb4773).

* For backups stored in [HPE StoreOnce Cloud Bank Storage](storeonce_supported_features.md) repositories, Veeam Plug-in for Proxmox VE supports only file-level restore.

* You cannot perform VM restore from a tape to Enter value. A tape backup needs to be returned to a supported repository to complete the restore operation.

* If you restore the VM from a backup stored in the archive tier of the scale-out backup repository, you must first retrieve backup data as described in the Veeam Backup & Replication User Guide, section [Retrieving Backup Files](https://helpcenter.veeam.com/docs/vbr/userguide/retrieval_job_launch.html?ver=13). Note that you cannot perform Entire VM restore from backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent. For those backups, you can perform [Instant VM Recovery](pve_restore_instant.md).

* Veeam Plug-in for Proxmox VE supports [Instant Recovery](pve_restore_instant.md) of Proxmox VE VMs to the VMware environment with the following limitations:

* UEFI VMs with MBR cannot be restored.
* Restored VMs may have an incorrect number of cores per vCPU assigned.
* Static IP addresses are not restored for Windows VMs.

* Veeam Plug-in for Proxmox VE does not support restore of VMs to the BTRFS and custom storage.


