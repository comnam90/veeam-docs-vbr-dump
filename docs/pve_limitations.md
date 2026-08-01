---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
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
* Veeam Plug-in for Proxmox VE does not support synchronization of date and time settings with the backup server — the AM/PM format is used by default and cannot be changed.

* The Proxmox VE server must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

* Before you [add a Proxmox VE server](pve_server_add.md) to the backup infrastructure, ensure that it has been assigned a unique Proxmox VE system UUID and its name does not contain an FQDN.

* If you want to protect VMs that reside in a Proxmox VE cluster, all nodes of this cluster must be added to the backup infrastructure separately. Adding clusters as standalone entities is not supported.
* After you add nodes of a cluster to the backup infrastructure, you must not change the name of the cluster in the Proxmox VE administration portal.
* After you make changes to your Proxmox VE environment (for example, you migrate a VM between cluster nodes), these changes may not appear in Veeam Backup & Replication immediately — the data synchronization process between the backup server and the Proxmox VE server may take up to 15 minutes to complete. You can speed up the data synchronization process by [rescanning the Proxmox VE server](pve_server_rescan.md).

Backup Repositories

When managing backup repositories, consider that Veeam Plug-in for Proxmox VE does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) repositories. However, you can use them for [storing copies of backups](pve_backups_copy.md) created with Veeam Plug-in for Proxmox VE.

Workers

When configuring workers, consider the following:

* The default local storage must be enabled on all hosts where worker VMs will be deployed. If you cannot use the default storage in your environment, contact [Veeam Customer Support](pve_export_logs.md).
* The storage where system files of workers will be stored must be file-level storage and must [support snapshots](https://pve.proxmox.com/wiki/Storage). LVM storage that uses the Snapshots as Volume Chains (SAVC) mechanism cannot be selected for storing worker files.
* When transferring VM data to and from backup repositories, workers rely on the Hot-Add and NBD transport modes.

Backup

When protecting Proxmox VE resources, consider the following:

* Veeam Plug-in for Proxmox VE does not support backup of LXC containers.

* Veeam Plug-in for Proxmox VE does not support backup of VM templates.
* Veeam Plug-in for Proxmox VE does not support backup of VMs with the same BIOS UUID.

* Veeam Plug-in for Proxmox VE does not support backup of iSCSI disks attached to VMs — such disks are skipped from backup processing.
* Veeam Plug-in for Proxmox VE does not support backup of directly attached (passthrough) disks. If such disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Proxmox VE does not support backup of VM permissions granted to users, user groups and API tokens.
* Veeam Plug-in for Proxmox VE does not support backup of VMs that store their disks in the BTRFS and custom storage. All other [Proxmox VE storage types](https://pve.proxmox.com/wiki/Storage) are supported.
* The number of concurrent backup operations performed in each storage is limited to 4 to avoid excessive load on the production environment. To change the limit, contact [Veeam Customer Support](pve_export_logs.md).

* Veeam Plug-in for Proxmox VE does not support the recovery run logic for periodic backup schedules with a backup window configured — no job session will start immediately after the denied period is over. Only midnight is used as [a reference time](backup_window.md) for periodically run jobs.
* Veeam Plug-in for Proxmox VE supports backup of VMs that store their disks in LVM-based storage if the Snapshots as Volume Chain (SAVC) mechanism is enabled.

Guest Processing

When configuring guest processing in backup jobs, consider the following:

* The file exclusion functionality is not supported.

* Veeam Plug-in for Proxmox VE cannot [use Kerberos authentication](https://helpcenter.veeam.com/docs/vbr/userguide/kerberos_authentication.html?ver=13) while connecting to guest OSes of the processed VMs.

* When restoring a database using Veeam Explorers to the original VM, the VM hostname is used instead of the FQDN name. If Veeam Explorers cannot reach the VM, you can add the FQDN name and the IP address of the VM to the hosts file on the backup server.
* If you import backups created by a job with guest processing enabled, this backup job will truncate transaction logs but it will not store transaction log backups in the repository. To avoid the issue, before running the job, either clone the job and perform active full, or contact Veeam Customer Support.
* Image-level, application-aware backups of Veeam Backup for Microsoft 365 servers running on Proxmox VE clusters are not Veeam Microsoft 365 restore explorers-aware. The behavior described in [this article](https://bp.veeam.com/vb365/guide/design/vb365_with_vbr) is currently unsupported for Proxmox VE backups.

* Veeam Plug-in for Proxmox VE will not be able to create an application-consistent backup of a Microsoft SQL Server running a Windows Server Failover Cluster. If you add such a VM to the backup job scope and enable application-aware processing for it, Veeam Backup & Replication will only create an image-level backup. To work around the limitation, [use Veeam Agent](agents_cluster_support.md) managed by Veeam Backup & Replication instead.

Replication

When configuring replication of Proxmox VE resources, consider the following:

* Replication operations are supported only on the Veeam Backup & Replication desktop console.
* Replication within the same cluster does not preserve MAC address of the original VM.
* If the original VM is missing disks that exist on the replica VM, Veeam Plug-in for Proxmox VE will automatically create the missing disks during failback. The missing disks will be placed on the Proxmox VE storage that supports VM disk creation and has the most available free space.
* Starting from version 9, Proxmox VE supports the [snapshot-as-volume-chain](https://pve.proxmox.com/wiki/Storage%3A_LVM) functionality for some storage types. Since this functionality is available for VMs using QEMU version 10 and later, Veeam Plug-in for Proxmox VE is not able to restore VMs using an earlier QEMU version to a storage with the Allow Snapshots as Volume-Chain setting enabled. To work around the issue, see [this Veeam KB article](https://www.veeam.com/kb4773).

Restore

When restoring Proxmox VE resources, consider the following:

* Starting from version 9, Proxmox VE supports the [snapshot-as-volume-chain](https://pve.proxmox.com/wiki/Storage%3A_LVM) functionality for some storage types. Since this functionality is available for VMs using QEMU version 10 and later, Veeam Plug-in for Proxmox VE is not able to restore VMs using an earlier QEMU version to a storage with the Allow Snapshots as Volume-Chain setting enabled. To work around the issue, see [this Veeam KB article](https://www.veeam.com/kb4773).

* For backups stored in [HPE StoreOnce Cloud Bank Storage](storeonce_supported_features.md) repositories, Veeam Plug-in for Proxmox VE supports only file-level restore.

* Veeam Plug-in for Proxmox VE does not support restore of High Availability (HA) VM settings.

* You cannot perform VM restore from a tape to Proxmox VE. A tape backup needs to be returned to a supported repository to complete the restore operation.

* If you restore the VM from a backup stored in the archive tier of the scale-out backup repository, you must first retrieve backup data as described in the Veeam Backup & Replication User Guide, section [Retrieving Backup Files](https://helpcenter.veeam.com/docs/vbr/userguide/retrieval_job_launch.html?ver=13). Note that you cannot perform Entire VM restore from backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent. For those backups, you can perform [Instant VM Recovery](pve_restore_instant.md).

* Veeam Plug-in for Proxmox VE supports [Instant Recovery](pve_restore_instant.md) of Proxmox VE VMs to the VMware environment with the following limitations:

* UEFI VMs with MBR cannot be restored.
* Restored VMs may have an incorrect number of cores per vCPU assigned.
* Static IP addresses are not restored for Windows VMs.

* Veeam Plug-in for Proxmox VE does not support restore of VMs to the BTRFS and custom storage.
* When performing restore of an entire VM that originally resided on a platform other than Proxmox VE, Veeam Plug-in for Proxmox VE tries to install VirtIO drivers that are required for VM boot. However, those drivers must be installed manually on VMs with VMDK disks.
* VirtIO driver injection for VMs restored to LVM Thin storage may take longer, depending on the disk size. If this causes issues, you can disable the feature by setting the EnableDriverInjectionPreCheck parameter to false in the appsettings.json file.

Instant Recovery

When restoring Proxmox VE resources with Instant Recovery, consider the following:

* You can perform instant recovery to VMware, Hyper-V or Nutanix AHV hosts from backups created by Veeam Plug-in for Proxmox VE. VMware vSphere, Hyper-V or Nutanix AHV hosts must be added to the Veeam Backup & Replication backup infrastructure.
* It is recommended to deploy a dedicated host as a mount server and allocate a minimum of 512 MB of additional RAM for each VM disk that you want to recover at the same time. For example, if you restore a VM with 4 disks, you need an additional 2 GB of RAM on the mount server.
* A Proxmox VE host must be added to the Veeam Backup & Replication backup infrastructure.
* Veeam Plug-in for Proxmox VE requires 64 MB of RAM for a VM to perform Instant Recovery. For VMs with less than 64 MB of RAM, Veeam Plug-in for Proxmox VE increases the amount of RAM to 64 MB during the restore process.
* If you perform Instant Recovery using a VM backup stored in the archive tier of the scale-out backup repository, you must first retrieve backup data as described in section [Retrieving Backup Files](retrieval_job_launch.md). Note that this requirement is not applicable to backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent.
* Veeam Plug-in for Proxmox VE does not support Instant Recovery to LVM storage when the Snapshots as Volume Chains (SAVC) mechanism is enabled on the target host. To perform Instant Recovery, use a different storage type that supports QCOW2 format as the restore destination.
* Instant Recovery is not supported:

* From backups of VMs with the ARM architecture.
* From file-level backups created by the Kasten platform, Veeam Agent for Linux, Veeam Agent for Microsoft Windows, Veeam Agent for Unix, Veeam Agent for Mac.

* VirtIO drivers must be installed initially before the instant recovery process. You cannot add or modify drives in the VM during Instant Recovery launch.

Page updated 2026-07-30

