---
title: "Infrastructure Icons"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/infrastructure_icons.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Infrastructure Icons


The user interface icons display Veeam Backup & Replication infrastructure objects, jobs and their current state.

Jobs

The following icons represent the jobs configured in Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/job.webp) | Job |
| ![Infrastructure Icons](images/high_priority_job.webp) | High priority job |
| ![Infrastructure Icons](images/job_disabled.webp) | Job in the disabled state |
| ![Infrastructure Icons](images/job_start.webp) | Job in the running state |

Job Nodes

The following icons represent the job nodes displayed in the inventory pane of the Home view.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/backup_jobs_backup.webp) | Backup jobs |
| ![Infrastructure Icons](images/backup_jobs_replication.webp) | Replication jobs |
| ![Infrastructure Icons](images/copy_job.webp) | Backup copy jobs |
| ![Infrastructure Icons](images/sbjob.webp) | SureBackup jobs |
| ![Infrastructure Icons](images/tape_job.webp) | Tape jobs |
| ![Infrastructure Icons](images/backup_jobs_filecopy.webp) | File copy jobs |
| ![Infrastructure Icons](images/backup_jobs_vmcopy.webp) | VM copy jobs |
| ![Infrastructure Icons](images/agent_backup_job.webp) | Agent backup jobs / backup copy jobs |

Backups

The following icons represent the backups created with Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/icon_full.webp) | Backup |
| ![Infrastructure Icons](images/encrypted_backup.webp) | Encrypted backup |
| ![Infrastructure Icons](images/file_to_tape_backup.webp) | Backup to tape |
| ![Infrastructure Icons](images/incomplete_backup.webp) | Incomplete backup |

Backup Nodes

The following icons represent the backup nodes displayed in the inventory pane of the Home view.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/backup_backups_disk.webp) | Backups on disk |
| ![Infrastructure Icons](images/backup_copy.webp) | Backup copies on disk |
| ![Infrastructure Icons](images/backup_backups_imported.webp) | Imported backups on disk |
| ![Infrastructure Icons](images/backup_disk_exported.webp) | Exported backups on disk |
| ![Infrastructure Icons](images/disk_orphaned.webp) | Orphaned backups on disks |
| ![Infrastructure Icons](images/encrypted_backups.webp) | Encrypted backups on disk |
| ![Infrastructure Icons](images/external_backups.webp) | Backups in external repository |
| ![Infrastructure Icons](images/external_encrypted_backups.webp) | Encrypted backups in external repository |
| ![Infrastructure Icons](images/cloud_backup.webp) | Backups in cloud repository |
| ![Infrastructure Icons](images/cloud_orphaned.webp) | Orphaned backups in cloud repository |
| ![Infrastructure Icons](images/backups_to_tape.webp) | Backups on tape |
| ![Infrastructure Icons](images/encrypted_tape_backups.webp) | Encrypted backups on tape |
| ![Infrastructure Icons](images/backups_object_storage.webp) | Backups in object storage |
| ![Infrastructure Icons](images/object_storage_copy.webp) | Backup copies in object storage |
| ![Infrastructure Icons](images/object_storage_encrypted.webp) | Encrypted backups in object storage |
| ![Infrastructure Icons](images/object_storage_imported.webp) | Imported backups in object storage |
| ![Infrastructure Icons](images/object_storage_ophaned.webp) | Orphaned backups in object storage |
| ![Infrastructure Icons](images/object_storage_veeamZIP.webp) | VeeamZIP backups in object storage |
| ![Infrastructure Icons](images/object_storage_archive.webp) | Backups in object storage with data archiving |
| ![Infrastructure Icons](images/capacity_tier.webp) | Backups in capacity tier |
| ![Infrastructure Icons](images/capacity_tier_imported.webp) | Imported backups in capacity tier |
| ![Infrastructure Icons](images/capacity_tier_orphaned.webp) | Orphaned backups in capacity tier |
| ![Infrastructure Icons](images/capacity_tier_veeamzip.webp) | VeeamZIP backups in capacity tier |
| ![Infrastructure Icons](images/archive.webp) | Backups in archive tier |
| ![Infrastructure Icons](images/archive_imported.webp) | Imported backups in archive tier |
| ![Infrastructure Icons](images/archive_orphaned.webp) | Orphaned backups in archive tier |
| ![Infrastructure Icons](images/archive_veeamzip.webp) | VeeamZIP backups in archive tier |

Restore Points

The following icons indicate the states of the restore points in backups of all types.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/icon_full.webp) | Full restore point |
| ![Infrastructure Icons](images/icon_forward_incremental.webp) | Incremental restore point |
| ![Infrastructure Icons](images/icon_reverse_incremental.webp) | Reverse incremental restore point |
| ![Infrastructure Icons](images/icon_full_unavailable.webp) | Missing full restore point |
| ![Infrastructure Icons](images/icon_forward_unavailable.webp) | Missing incremental restore point |
| ![Infrastructure Icons](images/icon_reverse_unavailable.webp) | Missing reverse incremental restore point |
| ![Infrastructure Icons](images/icon_restore_point_infected.webp) | Infected restore point |

Scale-Out Backup Repository Restore Points

The following icons indicate the states of the restore points in the scale-out backup repository.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/vbk.webp) | Full restore point; on performance tier only |
| ![Infrastructure Icons](images/vbk_rehydrated.webp) | Full restore point; on performance tier and offloaded to capacity tier |
| ![Infrastructure Icons](images/vbk_dehydrated.webp) | Full restore point; on capacity tier only |
| ![Infrastructure Icons](images/vbk_partially_rehydrated.webp) | Full restore point; on capacity tier and partially downloaded to performance tier  (This can happen when download to the performance tier fails) |
| ![Infrastructure Icons](images/vib.webp) | Incremental restore point; on performance tier only |
| ![Infrastructure Icons](images/vib_rehydrated.webp) | Incremental restore point; on performance tier and offloaded to capacity tier |
| ![Infrastructure Icons](images/vib_dehydrated.webp) | Incremental restore point; on capacity tier only |
| ![Infrastructure Icons](images/vib_partially_rehydrated.webp) | Incremental restore point; on capacity tier and partially downloaded to performance tier  (This can happen when download to the performance tier fails) |
| ![Infrastructure Icons](images/vrb.webp) | Rollback restore point; on performance tier only |
| ![Infrastructure Icons](images/vrb_rehydrated.webp) | Rollback restore point; on performance tier and offloaded to capacity tier |
| ![Infrastructure Icons](images/vrb_dehydrated.webp) | Rollback restore point; on capacity tier only |
| ![Infrastructure Icons](images/vrb_partially_rehydrated.webp) | Rollback restore point; on capacity tier and partially downloaded to performance tier  (This can happen when download to the performance tier fails) |
| ![Infrastructure Icons](images/icon_archive.webp) | Rollback restore point; on archive tier only |

Replicas

The following icons represent the replicas configured in Veeam Backup & Replication and displayed in the inventory pane of the Home view.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/backup_replicas_active.webp) | Replicas in the active state |
| ![Infrastructure Icons](images/backup_replicas_ready.webp) | Replicas in the ready state |
| ![Infrastructure Icons](images/failover-plan.webp) | Failover plan |
| ![Infrastructure Icons](images/cloud_failover.webp) | Cloud failover plan |

Microsoft Entra ID Backups

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/backup_entraID_tenant.webp) | Microsoft Entra ID tenant / Microsoft Entra ID tenant backup |
| ![Infrastructure Icons](images/backup_entraID_audit_log.webp) | Microsoft Entra ID audit and sign-in log backup |
| ![Infrastructure Icons](images/backup_entraID_corrupted.webp) | Microsoft Entra ID tenant backup is corrupted |

VMware vSphere Virtual Infrastructure

The following icons represent the hypervisor objects of VMware vSphere workloads and servers added to the backup infrastructure.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/vc.webp) | vCenter |
| ![Infrastructure Icons](images/vm.webp) | VM |
| ![Infrastructure Icons](images/vm_deleted.webp) | Deleted VM |
| ![Infrastructure Icons](images/vm_running.webp) | VM in the running state |
| ![Infrastructure Icons](images/vm_paused.webp) | VM in the paused state |
| ![Infrastructure Icons](images/vm_disabled.webp) | VM in the disabled state |
| ![Infrastructure Icons](images/vm_failback.webp) | VM in the failback state |
| ![Infrastructure Icons](images/vm_corrupted.webp) | VM is corrupted |
| ![Infrastructure Icons](images/VM_not_consistent.webp) | VM is not consistent |
| ![Infrastructure Icons](images/infected_VM_vs.webp) | Infected VM |
| ![Infrastructure Icons](images/vm_upgrade.webp) | VM in the upgrade state |
| ![Infrastructure Icons](images/vm_fault_tolerance.webp) | VM with the vSphere Fault Tolerance feature enabled |
| ![Infrastructure Icons](images/cluster.webp) | Cluster |
| ![Infrastructure Icons](images/datacenter.webp) | Datacenter |
| ![Infrastructure Icons](images/datastore.webp) | Datastore |
| ![Infrastructure Icons](images/datastore_failed.webp) | Failed datastore |
| ![Infrastructure Icons](images/host.webp) | ESXi host |
| ![Infrastructure Icons](images/provider-vdc.webp) | Provider VDC |
| ![Infrastructure Icons](images/rp.webp) | Resource pool |

Hyper-V Virtual Infrastructure

The following icons represent the hypervisor objects of Hyper-V workloads and servers added to the backup infrastructure.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/hv_cluster.webp) | Cluster |
| ![Infrastructure Icons](images/hv_cluster_corrupted.webp) | Corrupted cluster |
| ![Infrastructure Icons](images/hv_host.webp) | Host |
| ![Infrastructure Icons](images/hv_scvmm.webp) | SCVMM |
| ![Infrastructure Icons](images/hv_vm.webp) | VM |
| ![Infrastructure Icons](images/hv_vm_pause.webp) | VM in the paused state |
| ![Infrastructure Icons](images/hv_vm_run.webp) | VM in the running state |
| ![Infrastructure Icons](images/hv_vm_failback.webp) | VM in the failback state |
| ![Infrastructure Icons](images/hyperv_vm_error.webp) | VM is corrupted |
| ![Infrastructure Icons](images/infected_hyperv.webp) | Infected VM |
| ![Infrastructure Icons](images/hyperv_vm_upgrade.webp) | VM in the upgrade state |

VMware Cloud Director

The following icons represent the VMware Cloud Director objects added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/vcd_system.webp) | VMware Cloud Director infrastructure |
| ![Infrastructure Icons](images/vcd_organization.webp) | Cloud Director organization |
| ![Infrastructure Icons](images/vcd_organization_dc.webp) | Cloud Director organization VDC |
| ![Infrastructure Icons](images/vApp_off.webp) | Cloud Director vApp |
| ![Infrastructure Icons](images/vApp_on.webp) | Cloud Director vApp in the running state |
| ![Infrastructure Icons](images/vapp_not_consistet.webp) | Cloud Director vApp is not consistent |
| ![Infrastructure Icons](images/vapp_mounting.webp) | Cloud Director vApp in the mounting state |
| ![Infrastructure Icons](images/vapp_failback.webp) | Cloud Director vApp in the failback state |
| ![Infrastructure Icons](images/vapp_infected.webp) | Cloud Director vApp is infected |
| ![Infrastructure Icons](images/vapp_corrupted.webp) | Cloud Director vApp is corrupted |
| ![Infrastructure Icons](images/vapp_error.webp) | Cloud Director vApp has an error |
| ![Infrastructure Icons](images/vcd_vapp_template.webp) | Cloud Director vApp template |

Physical Infrastructure

The following icons represent the physical infrastructure objects added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/veeam_container.webp) | Protection group |
| ![Infrastructure Icons](images/veeam_container_disabled.webp) | Protection group in the disabled state |
| ![Infrastructure Icons](images/protected_container_outofdate.webp) | Protection group is outdated |
| ![Infrastructure Icons](images/protected_container_unavailable.webp) | Protection group is unavailable |
| ![Infrastructure Icons](images/unmanaged_agents.webp) | Unmanaged protection group |
| ![Infrastructure Icons](images/agent_machine.webp) | Veeam Agent computer |
| ![Infrastructure Icons](images/agent_machine_corrupted.webp) | Veeam Agent computer is corrupted |
| ![Infrastructure Icons](images/encrypted_agent_machine.webp) | Encrypted Veeam Agent computer |
| ![Infrastructure Icons](images/infected_agent_machine.webp) | Infected Veeam Agent computer |
| ![Infrastructure Icons](images/windows_agent_machine.webp) | Microsoft Windows-based Veeam Agent computer |
| ![Infrastructure Icons](images/windows_agent_machine_corrupted.webp) | Microsoft Windows-based Veeam Agent computer is corrupted |
| ![Infrastructure Icons](images/linux_agent_machine.webp) | Linux-based Veeam Agent computer |
| ![Infrastructure Icons](images/linux_agent_machine_corrupted.webp) | Linux-based Veeam Agent computer is corrupted |
| ![Infrastructure Icons](images/mac_agent_machine.webp) | macOS-based Veeam Agent computer |
| ![Infrastructure Icons](images/mac_agent_machine_corrupted.webp) | macOS-based Veeam Agent computer is corrupted |
| ![Infrastructure Icons](images/agent_machine_IBM.webp) | IBM AIX-based Veeam Agent computer |
| ![Infrastructure Icons](images/agent_machine_IBM_corrupted.webp) | IBM AIX-based Veeam Agent computer is corrupted |
| ![Infrastructure Icons](images/agent_machine_oracle_solaris.webp) | Oracle Solaris-based Veeam Agent computer |
| ![Infrastructure Icons](images/agent_machine_oracle_solaris_corrupted.webp) | Oracle Solaris-based Veeam Agent computer is corrupted |

Unstructured Data

The following icons represent the unstructured data sources added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/file_server.webp) | File server |
| ![Infrastructure Icons](images/nas_filer.webp) | NAS filer |
| ![Infrastructure Icons](images/file_share.webp) | File share |
| ![Infrastructure Icons](images/cifs_server.webp) | SMB file server |
| ![Infrastructure Icons](images/nfs_server.webp) | NFS file server |
| ![Infrastructure Icons](images/amazons3.webp) | Amazon S3 object storage |
| ![Infrastructure Icons](images/azurestorage.webp) | Microsoft Azure Blob storage |
| ![Infrastructure Icons](images/azure_data_lake.webp) | Microsoft Azure Data Lake storage |
| ![Infrastructure Icons](images/amazons3compatible.webp) | S3 compatible object storage |

Backup Proxies

The following icons represent the backup proxies added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/proxy_vmware.webp) | VMware / Hyper-V backup proxy |
| ![Infrastructure Icons](images/proxy_vmware_disabled.webp) | VMware / Hyper-V backup proxy is disabled |
| ![Infrastructure Icons](images/file_proxy.webp) | General-purpose backup proxy (for file shares) |
| ![Infrastructure Icons](images/Infrastructure_proxy_busy.webp) | Backup proxy is busy |
| ![Infrastructure Icons](images/Infrastructure_proxy_disabled.webp) | Backup proxy is disabled |
| ![Infrastructure Icons](images/Infrastructure_proxy_outofdate.webp) | Backup proxy is outdated |
| ![Infrastructure Icons](images/Infrastructure_proxy_unavailable.webp) | Backup proxy is unavailable |
| ![Infrastructure Icons](images/cdp_proxy.webp) | CDP proxy |
| ![Infrastructure Icons](images/cdp_proxy_disabled.webp) | CDP proxy is disabled |
| ![Infrastructure Icons](images/cdp_proxy_outdated.webp) | CDP proxy is outdated |
| ![Infrastructure Icons](images/cdp_proxy_unavailable.webp) | CDP proxy is unavailable |

Backup Repositories and Scale-Out Backup Repositories

The following icons represent the backup repositories and scale-out backup repositories added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/repositories.webp) | Backup repositories |
| ![Infrastructure Icons](images/externalrepositories.webp) | External repositories |
| ![Infrastructure Icons](images/cloud_repository.webp) | Cloud repositories |
| ![Infrastructure Icons](images/extendable_backup_repository.webp) | Scale-out backup repository |
| ![Infrastructure Icons](images/infrastructure_repository_busy.webp) | Repository is busy |
| ![Infrastructure Icons](images/infrastructure_repository_full.webp) | Repository is full |
| ![Infrastructure Icons](images/infrastructure_repository_outofdate.webp) | Repository is outdated |
| ![Infrastructure Icons](images/infrastructure_repository_unavailable.webp) | Repository is unavailable |
| ![Infrastructure Icons](images/infrastructure_repository_disabled.webp) | Repository in the maintenance mode |
| ![Infrastructure Icons](images/infrastructure_repository_sealed.webp) | Repository in the sealed mode |
| ![Infrastructure Icons](images/repository_windows_icon.webp) | Windows server repository |
| ![Infrastructure Icons](images/repository_linux_icon.webp) | Linux server repository |
| ![Infrastructure Icons](images/linuxhardenedrepository.webp) | Hardened repository |
| ![Infrastructure Icons](images/repository_shared.webp) | SMB share repository |
| ![Infrastructure Icons](images/repositoryNFS.webp) | NFS share repository |
| ![Infrastructure Icons](images/cloud_vault.webp) | Veeam Data Cloud Vault |
| ![Infrastructure Icons](images/cloud_vault_disabled.webp) | Veeam Data Cloud Vault in the maintenance mode |
| ![Infrastructure Icons](images/cloud_vault_sealed.webp) | Veeam Data Cloud Vault in the sealed mode |
| ![Infrastructure Icons](images/amazons3compatible.webp) | S3 compatible repository |
| ![Infrastructure Icons](images/amazons3compatible_disabled.webp) | S3 compatible repository in the maintenance mode |
| ![Infrastructure Icons](images/amazons3comp_sealedmode.webp) | S3 compatible repository in the sealed mode |
| ![Infrastructure Icons](images/amazon_glacier_compatible.webp) | S3 compatible repository with data archiving repository |
| ![Infrastructure Icons](images/amazon_glacier_compatible_disabled.webp) | S3 compatible repository with data archiving repository in the maintenance mode |
| ![Infrastructure Icons](images/amazon_glacier_compatible_sealed.webp) | S3 compatible repository with data archiving repository in the sealed mode |
| ![Infrastructure Icons](images/amazons3.webp) | Amazon S3 repository |
| ![Infrastructure Icons](images/amazons3disabled.webp) | Amazon S3 repository in the maintenance mode |
| ![Infrastructure Icons](images/amazons3sealedmode.webp) | Amazon S3 repository in the sealed mode |
| ![Infrastructure Icons](images/amazonglacier.webp) | Amazon Glacier repository |
| ![Infrastructure Icons](images/amazonglacier_disabled.webp) | Amazon Glacier repository in the maintenance mode |
| ![Infrastructure Icons](images/amazonglacier_sealed.webp) | Amazon Glacier repository in the sealed mode |
| ![Infrastructure Icons](images/s3_integrated.webp) | S3-integrated repository (using SOSAPI functionality) |
| ![Infrastructure Icons](images/s3_integrated_disabled.webp) | S3-integrated repository in the maintenance mode |
| ![Infrastructure Icons](images/s3_integrated_sealed.webp) | S3-integrated repository in the sealed mode |
| ![Infrastructure Icons](images/awssnowball.webp) | AWS Snowball Edge Storage repository |
| ![Infrastructure Icons](images/awssnowballdisabled.webp) | AWS Snowball Edge Storage repository in the maintenance mode |
| ![Infrastructure Icons](images/awssnowball_sealedmode.webp) | AWS Snowball Edge Storage repository in the sealed mode |
| ![Infrastructure Icons](images/ibmcloud.webp) | IBM Cloud repository |
| ![Infrastructure Icons](images/ibmcloud_disabled.webp) | IBM Cloud repository in the maintenance mode |
| ![Infrastructure Icons](images/ibmcloud_sealed.webp) | IBM Cloud repository in the sealed mode |
| ![Infrastructure Icons](images/archivetier_googlecloud.webp) | Google Cloud Storage repository |
| ![Infrastructure Icons](images/archivetier_googleclouddisabled.webp) | Google Cloud Storage repository in the maintenance mode |
| ![Infrastructure Icons](images/archivetier_googlecloudsealed.webp) | Google Cloud Storage repository in the sealed mode |
| ![Infrastructure Icons](images/azurestorage.webp) | Microsoft Azure Blob Storage repository |
| ![Infrastructure Icons](images/azurestoragedisabled.webp) | Microsoft Azure Blob Storage repository in the maintenance mode |
| ![Infrastructure Icons](images/azuresealedmode.webp) | Microsoft Azure Blob Storage repository in the sealed mode |
| ![Infrastructure Icons](images/azurearchivestorage.webp) | Microsoft Azure Archive Storage repository |
| ![Infrastructure Icons](images/azurearchivestorage_disabled.webp) | Microsoft Azure Archive Storage repository in the maintenance mode |
| ![Infrastructure Icons](images/azurearchivestorage_sealed.webp) | Microsoft Azure Archive Storage repository in the sealed mode |
| ![Infrastructure Icons](images/azure_databox.webp) | Microsoft Azure Data Box Storage repository |
| ![Infrastructure Icons](images/azure_databox_disabled.webp) | Microsoft Azure Data Box Storage repository in the maintenance mode |
| ![Infrastructure Icons](images/azure_databox_sealed.webp) | Microsoft Azure Data Box Storage repository in the sealed mode |
| ![Infrastructure Icons](images/eleven_eleven.webp) | 11:11 Cloud Object Storage repository |
| ![Infrastructure Icons](images/eleven_eleven_disabled.webp) | 11:11 Cloud Object Storage repository in the maintenance mode |
| ![Infrastructure Icons](images/eleven_eleven_sealed.webp) | 11:11 Cloud Object Storage repository in the sealed mode |
| ![Infrastructure Icons](images/wasabi.webp) | Wasabi repository |
| ![Infrastructure Icons](images/wasabidisabled.webp) | Wasabi repository in the maintenance mode |
| ![Infrastructure Icons](images/wasabisealed.webp) | Wasabi repository in the sealed mode |
| ![Infrastructure Icons](images/infinidat_logo.webp) | Infinidat InfiniGuard repository |
| ![Infrastructure Icons](images/infinidat_disabled.webp) | Infinidat InfiniGuard repository in the maintenance mode |
| ![Infrastructure Icons](images/infinidat_sealed.webp) | Infinidat InfiniGuard repository in the sealed mode |
| ![Infrastructure Icons](images/quantumrepository.webp) | Quantum DXi repository |
| ![Infrastructure Icons](images/quantumrepository_disabled.webp) | Quantum DXi repository in the maintenance mode |
| ![Infrastructure Icons](images/quantumrepository_sealed.webp) | Quantum DXi repository in the sealed mode |
| ![Infrastructure Icons](images/storage_exagrid.webp) | ExaGrid repository |
| ![Infrastructure Icons](images/exagrid_repository_disable.webp) | ExaGrid repository in the maintenance mode |
| ![Infrastructure Icons](images/storage_exagrid_sealed.webp) | ExaGrid repository in the sealed mode |
| ![Infrastructure Icons](images/fujitsu_logo.webp) | Fujitsu ETERNUS CS800 repository |
| ![Infrastructure Icons](images/fujitsu_disabled.webp) | Fujitsu ETERNUS CS800 repository in the maintenance mode |
| ![Infrastructure Icons](images/fujitsu_sealed.webp) | Fujitsu ETERNUS CS800 repository in the sealed mode |
| ![Infrastructure Icons](images/hp_storeonce_repository.webp) | HPE StoreOnce repository |
| ![Infrastructure Icons](images/hp_storeonce_repository_disable.webp) | HPE StoreOnce repository in the maintenance mode |
| ![Infrastructure Icons](images/hp_storeonce_repository_sealed.webp) | HPE StoreOnce repository in the sealed mode |
| ![Infrastructure Icons](images/dell.webp) | Dell Data Domain repository |
| ![Infrastructure Icons](images/storage_DELL_disable.webp) | Dell Data Domain repository in the maintenance mode |
| ![Infrastructure Icons](images/storage_DELL_sealed.webp) | Dell Data Domain repository in the sealed mode |

External Repositories

The following icons represent the external repositories added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/amazon_s3external_repository.webp) | Amazon S3 external repository |
| ![Infrastructure Icons](images/azure_external_repository.webp) | Microsoft Azure Blob Storage external repository |
| ![Infrastructure Icons](images/google_cloud_external_repository.webp) | Google Cloud Storage external repository |
| ![Infrastructure Icons](images/external_repo_outofdate.webp) | External repository is unavailable |

WAN Accelerators

The following icons represent the WAN accelerators added to Veeam Backup & Replication.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/wan_accelerator.webp) | WAN accelerator |
| ![Infrastructure Icons](images/wan_accelerator_busy.webp) | WAN accelerator is busy |
| ![Infrastructure Icons](images/wan_accelerator_error.webp) | WAN accelerator has an error |
| ![Infrastructure Icons](images/wan_accelerator_outofdate.webp) | WAN accelerator is outdated |

SureBackup

The following icons represent the SureBackup objects.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/app_groups.webp) | Application group |
| ![Infrastructure Icons](images/virtual_labs.webp) | Virtual lab |

Managed Servers

For more information about the icons that represent the hypervisor objects of VMware vSphere workloads and servers, see the [VMware vSphere Virtual Infrastructure](#vi_vsphere) section.

For more information about the icons that represent the hypervisor objects of Hyper-V workloads and servers, see the [Hyper-V Virtual Infrastructure](#vi_hyperv) section.

| Icon | Description |
| --- | --- |
| ![Infrastructure Icons](images/windows_host.webp) | Microsoft Windows server |
| ![Infrastructure Icons](images/linux_host.webp) | Linux host |
| ![Infrastructure Icons](images/windows_host_failed.webp) | Server is unavailable |
| ![Infrastructure Icons](images/windows_host_warning.webp) | Server is outdated |
| ![Infrastructure Icons](images/vsa.webp) | Veeam Software Appliance |
| ![Infrastructure Icons](images/vsa_updates.webp) | Veeam Software Appliance is outdated |
| ![Infrastructure Icons](images/domain.webp) | Domain |

Tape Infrastructure

For more information about the icons that represent the tape infrastructure components, see [Tape Infrastructure Icons](tape_indicators.md).


