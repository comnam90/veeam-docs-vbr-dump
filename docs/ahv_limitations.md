---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_limitations.html"
last_updated: "2/3/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for Nutanix AHV, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for Nutanix AHV, consider the following:

* In the case where a Veeam Backup & Replication certificate is changed it will be necessary to restart the Veeam AHV service in order to facilitate proper internal component communications.
* Veeam ONE 13 supports monitoring, alerting and reporting features for AHV VMs. For the list of supported features, see the [What’s New document for Veeam ONE 13](https://www.veeam.com/veeam_one_13_whats_new_wn.pdf).
* You can use [Veeam Backup Enterprise Manager](https://helpcenter.veeam.com/docs/vbr/em/introduction.html?ver=13) to file-level restore guest OS files of Nutanix AHV VMs and manage Nutanix AHV VM backup copy jobs. All other operations are not supported.

* Veeam Plug-in for Nutanix AHV does not support the IPv6 protocol.

* The Nutanix AHV server must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

Backup Repositories

When configuring repositories for Nutanix AHV VM backups, consider the following:

* Veeam Plug-in for Nutanix AHV does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) and [HPE Cloud Bank Storage](storeonce_supported_features.md) repositories. However, you can use them for [storing copies of backups](ahv_backup_copy.md) created with Veeam Plug-in for Nutanix AHV. You can also use [Instant Recovery](ahv_instant_recovery_ahv.md) to restore VMs to Nutanix AHV from those or external repositories.
* If a standalone Veeam Backup & Replication repository extent storing Nutanix AHV VM backups is migrated into a scale-out backup repository, backup jobs will fail. To avoid the issue, [update the target repository](ahv_editing_jobs.md) in backup jobs.
* Only file-level restores are available for backups created by Veeam Plug-in for Nutanix AHV on HPE Cloud Bank Storage

Workers

When configuring workers, consider the following:

* UEFI boot is required for workers.
* Multiple vNICs may be configured for workers.
* For Prism Central deployments, the “SelfServiceContainer” storage container will always be used for workers.
* By default, installing worker updates is performed on each worker start. However, you can [disable automatic updates](ahv_workers_update.md),for example, if your infrastructure does not have connection to Internet.
* Workers may start on the same host if automatic host affinity is enabled, and the number of workers has exceeded the number of hosts in the cluster.

* [Applies only to the [Prism Central](ahv_infrastructure_prism_central.md) deployment] Worker image distribution is optimized so that the image is only populated to a Prism Central-managed cluster when a worker is instantiated on that cluster.
* If you raise the number of concurrent backup tasks on workers, backup jobs may fail due to CVM resource limitations. The CVM on each node of the cluster may need additional resources.

Backup

When protecting Nutanix AHV resources, consider the following:

* Veeam Plug-in for Nutanix AHV creates forward incremental per-VM backup chains (one backup chain contains data for one VM). When you add several VMs to a backup job, Veeam Plug-in for Nutanix AHV creates individual backup chains on the Veeam backup repository, one for each VM processed by the job. Note that for forward incremental backup chains, you can create active or synthetic full backups. For more information, see [Backup Methods](backup_methods.md).
* By default, Veeam Plug-in for Nutanix AHV applies the following deduplication and compression settings to backed-up data:

* Deduplication: Enabled
* Data compression level: Optimal
* Storage optimization: 1MB

Due to technical limitations, you cannot change deduplication settings while configuring backup jobs.

* By default, backup encryption is disabled for backed-up data. However, you can enable encryption at the repository level. For more information, see [Access Permissions](access_permissions.md).
* Since Veeam Backup & Replication does not allow you to assign [information about locations](locations.md) to Nutanix AHV clusters, job statistics do not include information on the Nutanix AHV VM data migration between different geographic regions.
* Manual Move backup functionality is not supported for Nutanix AHV backups.
* If you add a Prism Central category to a backup job, VMs that are assigned to this category will be processed in size order starting with the largest one.

* If you specify a VM as the source for a backup job, Veeam Plug-in for Nutanix AHV processes volume groups attached to the VM. However, if you back up the VM with the attached volume groups, Veeam Plug-in for Nutanix AHV will create a crash-inconsistent backup.
* Veeam Plug-in for Nutanix AHV does not process volume groups if CHAP authentication is enabled. For more information, see [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:wc-volume-group-configure-c.html).
* Second [Health Check](ahv_how_health_check_works.md) of same data corruption returns successful session (disk is skipped from processing).
* Backups cannot be imported from unsupported repository types. This can affect importing from backup copy jobs.
* Backup Copy exclusions cannot be applied to Nutanix AHV jobs and objects.
* For VeeamZIP backups, retention is not supported.
* For VeeamZIP backups, an SMB share that requires authentication cannot be specified as a local or shared folder. However, it can be added to the backup infrastructure and then set as backup repository.
* [SureBackup](surebackup_recovery_verification.md) for backups created by Veeam Plug-in for Nutanix AHV is supported in the Backup verification and content scan only verification mode.

* Nutanix CVM cannot be backed up with Veeam Plug-in for Nutanix AHV.
* Veeam Plug-in for Nutanix AHV does not support the Migrate Across Clusters functionality. If a VM is migrated in this way, backup jobs that contain this VM will skip it. If the VM is included into a category, a backup job that protects this category will start a new backup chain for the migrated VM.

Backup From Replica Cluster

When configuring backup jobs to use backups from [replica clusters](ahv_backup_job_vbr_assign_vms.md), consider the following:

* Backup from a replica cluster can be used if a protection policy is configured in Prism Central.
* Backup from replica cluster will not be performed if guest processing (application-aware processing or indexing) is enabled in the backup job.
* If backup cannot be performed from a replica cluster, it will be performed from the original cluster.
* If there is no replicated snapshot on a replica cluster, backup will be performed from the original cluster.
* VMs with volume groups attached cannot be backed up from a replica cluster.
* If VM disks were added or removed after the last replication, VM backup will be performed from the original cluster.
* PD snapshots created using Nutanix AHV Async DR are not supported.

Guest Processing

When configuring guest processing in backup jobs, consider the following:

* Database log shipping: When upgrading from plug-in version 7.1 the parent backup job must be run to re-initiate log shipping.
* Pre-job and post-job scripts are not supported.
* The .JS, .VBS and .WSF scripts are not supported for pre-freeze and post-thaw (snapshot) operations.
* Persistent guest agent are supported in non-FIPS mode only.
* The file exclusion functionality is not supported.

* Veeam Plug-in for Nutanix AHV cannot [use Kerberos authentication](kerberos_authentication.md) while connecting to guest OSes of the processed VMs.

* When restoring a database using Veeam Explorers to the original VM, the VM hostname is used instead of the FQDN name. If Veeam Explorers cannot reach the VM, you can add the FQDN name and the IP address of the VM to the hosts file on the backup server.
* If you import backups created by a job with guest processing enabled, this backup job will truncate transaction logs but it will not store transaction log backups in the repository. To avoid the issue, before running the job, either clone the job and perform active full, or contact contact Veeam Customer Support.
* Image-level, application-aware backups of Veeam Backup for Microsoft 365 servers running on Nutanix AHV clusters are not Veeam Microsoft 365 restore explorers-aware. The behavior described in [this article](https://bp.veeam.com/vb365/guide/design/vb365_with_vbr) is currently unsupported for AHV backups.

* Veeam Plug-in for Nutanix AHV will not be able to create an application-consistent backup of a Microsoft SQL Server running a Windows Server Failover Cluster. If you add such a VM to the backup job scope and enable application-aware processing for it, Veeam Backup & Replication will only create an image-level backup. To work around the limitation, [use Veeam Agent](agents_cluster_support.md) managed by Veeam Backup & Replication instead.

Restore

When restoring Nutanix AHV resources, consider the following:

* If you restore the VM to Nutanix AOS 7.0 or later, the [SCSI Controller](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide:ahv-disable-scsi-controller-c.html) and the [CPU hot-plug functionality](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide:ahv-disable-cpu-hot-plug-c.html) are always enabled (the scsi\_controller\_enabled and cpu\_hotplug\_enabled parameters are automatically set to true).
* If you restore the VM with an affinity policy not to the original cluster, you must manually configure the affinity policy manually before starting the recovered VM. For more information on affinity policies, see [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:ahv-affinity-policies-c.html).
* If you restore the VM from a snapshot of any type, you cannot change the storage container.
* If you restore the VM using entire VM restore, the VM description will not be restored (will be set as empty).
* If you restore the VM from a user snapshot or PD snapshot, you cannot change VM network settings. However, after the VM is restored, you can configure them using the Nutanix Prism console as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v10_3:ahv-vm-nw-mgmt-c.html). If you choose to restore to different location and choose to disconnect from all networks, the new VM will be created without networks.
* If you restore the VM from a backup stored in the archive tier of the scale-out backup repository, you must first retrieve backup data as described in section [Retrieving Backup Files](retrieval_job_launch.md). Note that you cannot perform Entire VM restore from backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent. For those backups, you can perform Instant Recovery.
* If you restore the VM from a backup of a VMware, Hyper-V, oVirt KVM, Scale Computing HyperCore or Proxmox VE VM or from a backup created by Veeam Agent, a restored VM may have network connection problems. To resolve the issue, install Nutanix Guest Tools on the restored VM as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:man-nutanix-guest-tool-c.html).
* You cannot perform Entire VM Restore to Nutanix AHV from a Veeam Cloud Connect repository or an external repository. However, you can use Instant Recovery to restore VMs to Nutanix AHV from Veeam Cloud Connect or external repositories.
* You cannot perform VM restore from a tape to Nutanix AHV. A tape backup needs to be returned to a supported repository to complete the restore operation.
* You cannot perform VM restore from PD snapshots created using Nutanix AHV Async DR.
* If you want to perform file-level restore from volume group disks, you should run FLR from backups of the VM that have the required volume group attached to them.

Instant Recovery

When restoring Nutanix AHV resources with Instant Recovery, consider the following:

* You can perform instant recovery to VMware and Hyper-V hosts from backups created by Veeam Plug-in for Nutanix AHV. VMware vSphere or Hyper-V hosts must be added to the Veeam Backup & Replication backup infrastructure.
* It is recommended to deploy a dedicated host as a mount server and allocate a minimum of 512 MB of additional RAM for each VM disk that you want to recover at the same time. For example, if you restore a VM with 4 disks, you need an additional 2 GB of RAM on the mount server.
* A Nutanix AHV cluster must be added to the Veeam Backup & Replication backup infrastructure.
* Veeam Plug-in for Nutanix AHV requires 64 MB of RAM for a VM to perform Instant Recovery. For VMs with less than 64 MB of RAM, Veeam Plug-in for Nutanix AHV increases the amount of RAM to 64 MB during the restore process.
* If you perform Instant Recovery using a VM backup stored in the archive tier of the scale-out backup repository, you must first retrieve backup data as described in section [Retrieving Backup Files](retrieval_job_launch.md). Note that this requirement is not applicable to backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent.
* If you restore a Nutanix AHV VM that has an attached volume group, the disks from the volume group will not be restored.
* Instant Recovery is not supported:

* From backups created by Veeam Availability for Nutanix AHV (Veeam Plug-in for Nutanix AHV version 1.0). For those backups, you can perform only entire VM restore.
* From backups of VMs with the ARM architecture.
* From file-level backups created by the Kasten platform, Veeam Agent for Linux, Veeam Agent for Microsoft Windows, Veeam Agent for Unix, Veeam Agent for Mac.

* Nutanix VirtIO drivers should be installed initially before the instant recovery process. You cannot add or modify drives in the VM during Instant Recovery launch.

REST API Limitations

When using REST API for protecting Nutanix AHV resources, consider the following:

* REST API versions earlier than 8 are not supported.
* You cannot obtain information on ordinary backup restore point ID. Use Power Shell instead.
* You cannot use an account with MFA enabled to obtain an authorization token.
* You cannot enable MFA for a user account.


