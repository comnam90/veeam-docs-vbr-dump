---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


|  |
| --- |
| Important |
| Veeam Backup for Microsoft Azure does not support Microsoft Azure features that are currently in the preview state. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops). |

When you plan to deploy and configure backup appliances, keep in mind the following limitations and considerations.

Hardware

Hardware

| Component | Recommended Azure VM size |
| Backup appliance | * Standard\_B2s with 2 CPUs and 4 GB RAM * Standard\_B2ms with 2 CPUs and 8 GB RAM |
| Worker instances | * Standard\_F2s\_v2 with 2 CPUs and 4 GB RAM for regular backup * Standard\_E2\_v5 with 2 CPUs and 16 GB RAM for archived backup |

For more information on Azure VM sizes, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes-general).

Software

To access backup appliance, use Microsoft Edge (latest version), Mozilla Firefox (latest version) or Google Chrome (latest version). Internet Explorer is not supported.

Security Certificates

Backup appliances supports certificates in the formats .PFX and .P12.

Backup Appliances

When deploying backup appliances, consider the following:

* Veeam Plug-in for Microsoft Azure does not support the deployment of backup appliances using Microsoft Azure compute accounts registered in China. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/china/).

Repositories

When managing repositories, consider the following:

* Veeam Plug-in for Microsoft Azure does not support creation of backup repositories in storage accounts with the [Azure Data Lake Storage Gen2 hierarchical namespace](https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-namespace) enabled.
* Veeam Plug-in for Microsoft Azure does not support creation of backup repositories in storage accounts with the [container soft delete](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-container-overview) option enabled.
* Veeam Plug-in for Microsoft Azure does not support creation of backup repositories in storage accounts with the [blob soft delete](https://docs.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview#recommended-data-protection-configuration) option enabled.
* Veeam Plug-in for Microsoft Azure does not support creation of backup repositories in the Cold access tier. For more information on access tiers for blob data, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview).
* Veeam Plug-in for Microsoft Azure does not support creation of mutable backup repositories in storage accounts with the [blob versioning](https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-overview) option enabled. To use an account with blob versioning enabled, consider that this may result in extra costs for storing objects that have been removed by the retention policy.
* Due to Microsoft Azure limitations, Veeam Plug-in for Microsoft Azure does not support creation of archive repositories in storage accounts with the [Zone-redundant storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy#zone-redundant-storage) (ZRS), [Geo-zone-redundant storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy#geo-zone-redundant-storage) (GZRS) or [Read-access geo-zone-redundant storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy#read-access-to-data-in-the-secondary-region) (RA-GZRS) redundancy option enabled. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview#archive-access-tier).
* Veeam Plug-in for Microsoft Azure does not support copying backed-up data from one Azure blob container to another using Microsoft Azure tools and adding the new container as a repository.
* By default, Veeam Backup for Microsoft Azure does not download and check the Certificate Revocation List (CRL) files of storage accounts when creating backup repositories. If you want to instruct Veeam Backup for Microsoft Azure to download and check these files, open a [support case](azure_support_information.md).

* Veeam Plug-in for Microsoft Azure does not support adding one backup repository to multiple backup appliances simultaneously.
* If you move a storage account in which a backup repository was created to another resource group and remove the original resource group from Microsoft Azure, all operations related to that repository will fail.
* It is recommended that you use a dedicated storage account for backup repositories where Veeam Backup for Microsoft Azure will store backed-up data. Otherwise, Veeam Backup for Microsoft Azure may fail to recover the data due to folder synchronization issues.
* To use a [Veeam Data Cloud storage vault](azure_vdc_vaults.md) as a target location for backed-up data, you must [get access to Veeam Data Cloud Vault](https://helpcenter.veeam.com/docs/vdc/userguide/vault_obtain_product.html) and [connect your backup appliance to the necessary storage vault](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#assigning-storage-vaults-to-workloads) as described in the Veeam Data Cloud User Guide, section Veeam Data Cloud Vault.

Network Settings for Worker Instances

When adding worker configurations, consider the following:

* A virtual network service endpoint (routing) for the Microsoft.Storage.Global service must be configured for virtual networks to which worker instances will be connected — you can either configure the endpoint manually in Microsoft Azure beforehand or let Veeam Backup for Microsoft Azure do it for you automatically while deploying the worker instances. To learn how to configure virtual network service endpoints manually, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview).
* The subnet to which worker instances will be connected must have at least one free IP address in the subnet range — Veeam Backup for Microsoft Azure will be able to launch and simultaneously run as many worker instances as many free IP addresses there are in the subnet range. If your backup appliance is deployed in a private environment, the subnet to which worker instances will be connected must have at least 3 free IP addresses and 4 free private endpoints in the subnet range.
* By default, worker instances use public endpoints to connect to Azure SQL Managed Instances through port 3342. If a worker tries to connect to an Azure SQL Managed Instance and public endpoints are disabled for this instance, the worker will use a private endpoint to connect to the instance through port 1433 instead. However, for the worker to be able to establish the connection, virtual networks to which the worker and the Azure SQL Managed Instance are connected must be peered in the Microsoft Azure portal. To learn how to peer virtual networks, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/tutorial-connect-virtual-networks-portal#peer-virtual-networks).
* For each automatically created worker configuration, Veeam Backup for Microsoft Azure creates a virtual network, a subnet and a network security group.
* It is not recommended that you manually change settings of automatically created configurations. If you want to use a specific worker configuration, add it manually as described in section [Adding Worker Configurations](azure_worker_configuration_add.md).

For more information on worker configurations, see [Managing Worker Instances](azure_workers.md).

Backup

When backing up Azure resources, consider the following:

* If you specify a management group as [the service account scope](azure_service_account_scope.md), Veeam Backup for Microsoft Azure can include in the backup scope only those Azure subscriptions that are located one level lower under the selected management group.
* Health check cannot be performed for encrypted backups with missing metadata files, or for backups with corrupted metadata files.
* Veeam Backup Enterprise Manager does not support management of backup policies created in Veeam Backup for Microsoft Azure.
* If you choose to back up Azure resources that are managed by specific subscriptions, belong to specific resource groups or have specific tags assigned, it may take up to 24 hours for Veeam Backup for Microsoft Azure to detect resources that either are newly deployed in the specified subscriptions and resource groups or recently have the specified tags assigned. To speed up this process and update the backup scope list, rescan the resources as described in section [Performing Backup](azure_backup.md).

* Since backup appliances runs retention sessions at 12:00 AM according to the time zone set on the backup appliance, it is not recommended that you schedule backup policies to execute at 12:00 AM. Otherwise, backup appliances may not be able to run retention sessions.
* Due to Microsoft Azure limitations, retention of [locked Azure VM snapshots](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json) is not supported. As a workaround, you can instruct Veeam Backup for Microsoft Azure to store snapshots in an unlocked resource group as described in [Creating SLA-Based VM Backup Policies](azure_vm_sla_tags_snapshot_location.md#location).

VM Backup

When backing up Azure VMs, consider the following:

* Before you create an Azure VM policy, make sure the Azure VMs you plan to protect have the [Azure Windows VM Agent](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows) (for Windows-based VMs) or [Azure Linux VM Agent](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-linux) (for Linux-based VMs) installed. Otherwise, Veeam Backup for Microsoft Azure will fail to create transactionally consistent snapshots for these VMs, and you will not be able to use any restore points produced for these VMs to perform file-level recovery to the original location. For more information on transactionally consistent snapshots, see [Specifying Guest Processing Settings](azure_vm_guest_processing.md).
* In versions prior to 8, Veeam Backup for Microsoft Azure created locally redundant snapshots for all Azure VMs by default, regardless of the source region. Starting from version 8, Veeam Backup for Microsoft Azure creates zone-redundant snapshots — but only for those Azure VMs that reside in regions with availability zone support enabled. When protecting VMs that reside in regions with availability zone support disabled, Veeam Backup for Microsoft Azure still creates locally redundant snapshots. For the list of Azure regions, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/reliability/regions-list#azure-regions-list-1).
* Veeam Plug-in for Microsoft Azure prioritizes SLA-based backup policies over schedule-based backup policies. If an Azure VM is included into both a schedule-based and an SLA-based backup policy, it will be processed by the SLA-based backup policy only.

* Since backup appliances runs retention sessions for SLA-based backup policies as soon as it finalizes the backup window in all protected regions, it is recommended that you estimate how long it may take for the appliance to complete a retention session first, and then configure a backup window. Otherwise, the backup appliance will not be able to run retention sessions, and obsolete data will not be removed from the configuration database and backup repositories.

* Veeam Backup for Microsoft Azure does not support backup of Azure VMs whose source disks have the data access authentication mode enabled. For more information on the data access authentication mode, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/download-vhd?tabs=azure-portal#enable-data-access-authentication-mode).
* Due to Microsoft Azure limitations, Veeam Backup for Microsoft Azure does not support backup of [Ephemeral OS disks](https://learn.microsoft.com/en-us/azure/virtual-machines/ephemeral-os-disks#unsupported-features).
* Due to Microsoft Azure limitations, you can apply up to 50 tags directly to a subscription. That is why Veeam Backup for Microsoft Azure is able to create a snapshot only if the tag limit is not reached for the subscription to which the processed Azure VM belongs. If the limit is reached, the operation will fail with a serialization error. For more information on subscription limits, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#subscription-limits).
* Unmanaged disks will be retired in Microsoft Azure on March 31, 2026. That is why it is recommended that you migrate your Azure VMs to managed disks. For more information, see [Microsoft Docs](https://learn.microsoft.com/el-gr/azure/virtual-machines/unmanaged-disks-deprecation).

SQL Backup

When backing up Azure SQL databases, consider the following:

* You can create SQL backup policies to protect only Azure SQL databases running on SQL Servers and databases located on SQL Managed Instances. If you want to protect a database hosted by a SQL Server on Azure VM, create an [Azure VM backup policy](azure_performing_vm_backup.md). Note that in this case, you will not be able to restore a single database without restoring the entire VM.
* Veeam Backup for Microsoft Azure does not support using staging servers to back up [free offer Azure SQL databases](https://learn.microsoft.com/en-us/azure/azure-sql/database/free-offer?view=azuresql).
* Veeam Backup for Microsoft Azure does not support backup of databases hosted by Azure Arc-enabled SQL Managed Instances and SQL Servers on Azure Arc-enabled servers.
* Veeam Backup for Microsoft Azure uses BACPAC files to back up SQL databases. BACPAC export of databases with external references is not supported. That is why if a SQL database was migrated to an Azure SQL Database Server or Azure SQL Managed Instance, make sure to clear legacy references, orphaned database users and credentials set up with authentication types not supported by Azure SQL, to avoid BACPAC export errors.

* Database accounts used to back up SQL databases must have the following roles assigned: the ##MS\_DatabaseManager##, ##MS\_LoginManager##, ##MS\_DatabaseConnector## and ##MS\_DefinitionReader## server-level roles, and the db\_owner database-level role. For more information on [server-level roles](https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver16) and [database-level roles](https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/database-level-roles?view=sql-server-ver16), see Microsoft Docs.
* Due to export process limitations, it is recommended that you back up Azure SQL databases up to 16 TB in size for optimal reliability. Backup of larger databases has not been tested and may not be supported.

Cosmos DB Backup

When backing up Cosmos DB accounts, consider the following:

* Veeam Backup for Microsoft Azure allows you to protect only Cosmos DB accounts created using the following APIs: NoSQL, MongoDB RU-based, Apache Gremlin, Table and PostgreSQL.
* Veeam Backup for Microsoft Azure does not support backup of Cosmos DB accounts that have [periodic backup](https://learn.microsoft.com/en-us/azure/cosmos-db/periodic-backup-restore-introduction) or [multi-region writes](https://learn.microsoft.com/en-us/azure/cosmos-db/how-to-manage-database-account#configure-multiple-write-regions) enabled.
* Due to Microsoft Azure limitations, Veeam Backup for Microsoft Azure does not support restore of Cosmos DB accounts encrypted using [customer-managed keys](https://learn.microsoft.com/en-us/azure/cosmos-db/how-to-setup-customer-managed-keys?tabs=azure-portal).

* Database accounts used to back up Cosmos DB for PostgreSQL accounts must have any role that has administrative permissions assigned; it is recommended that you use an account that has the built-in citus role assigned. For more information on native PostgreSQL roles, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/cosmos-db/postgresql/how-to-configure-authentication?tabs=portal).

Azure Files Backup

When backing up Azure file shares, consider the following:

* Due to Microsoft Azure limitations, Veeam Backup for Microsoft Azure does not support backup of [NFS Azure file shares](https://learn.microsoft.com/en-us/azure/storage/files/files-nfs-protocol).
* If you delete a file share from Microsoft Azure, all the snapshots of this file share will be deleted as well. To protect your snapshots from accidental deletion, you can use the file share soft delete option. For more information on the soft delete option for Azure Files, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-enable-soft-delete?tabs=azure-portal).
* Before you create an Azure Files policy, make sure the Allow storage account key access option for Shared Key authorization is enabled for the storage accounts where the file shares you plan to protect reside — otherwise, backup operations will fail. For more information on Shared Key authorization, see [Microsoft Docs](https://learn.microsoft.com/en-us/rest/api/storageservices/authorize-with-shared-key?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&bc=%2Fazure%2Fstorage%2Fblobs%2Fbreadcrumb%2Ftoc.json).
* When performing indexing operations, Veeam Backup for Microsoft Azure uses the Server Message Block (SMB) 3.0 and New Technology LAN Manager (NTLM) v2 protocols to authenticate against the processed file shares. For more information on SMB security settings, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/files/files-smb-protocol?tabs=azure-portal#smb-security-settings).

Restore

When restoring Azure resources, consider the following:

* When performing restore operations, Veeam Backup for Microsoft Azure assigns Azure tags to the processed resources. If you have any Azure policies that do not allow tag assignment, the restore operations will fail. That is why it is recommended that you do not configure such policies in Microsoft Azure. For more information on Azure policies, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/governance/policy/overview).
* Veeam Backup for Microsoft Azure does not support performing [Instant Recovery](azure_performing_instant_recovery.md) using backups stored in [Veeam Data Cloud storage vaults](azure_vdc_vaults.md) — you can only perform this restore operation using backups stored in standard backup repositories for which you have specified credentials of Microsoft Azure storage accounts where the target blob containers reside.
* Veeam Backup for Microsoft Azure does not support using backups that are stored in [Veeam Data Cloud storage vaults](azure_vdc_vaults.md) to perform the following restore operations: [guest OS file restore](azure_guest_file_recovery.md), [application restore](azure_application_items_restore.md), [disk export](azure_exporting_disks.md), [disk publishing](azure_publishing_disks.md), [restore to AWS](azure_restoring_to_amazon.md), [restore to Google Cloud](azure_restoring_to_google.md), [restore to Nutanix AHV](azure_restoring_to_nutanix.md), [Instant Recovery](azure_performing_instant_recovery.md). To perform these operations, use backups that are stored in standard backup repositories for which you have specified Microsoft Azure storage account credentials.

To learn how to specify credentials for repositories, see sections [Creating New Repositories](azure_repository_console_storage_account.md) and [Connecting to Existing Appliances](azure_adding_appliance_repository.md).

VM Restore

When restoring Azure VMs, consider the following:

* When performing [disk restore](azure_vm_restore_disk_hiw.md) to a new location from a cloud-native snapshot or image-level backup, Veeam Backup for Microsoft Azure does not attach the restored virtual disks to any Azure VM — the disks are placed to the specified location as standalone virtual disks.

* Veeam Backup for Microsoft Azure does not support restore to the original location of locked Azure VMs and Azure virtual disks. For more information on the lock feature, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json).
* Veeam Backup for Microsoft Azure does not support restore of Azure confidential VMs. For more information on Azure confidential VMs, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-overview).

SQL Restore

When restoring Azure SQL databases, consider the following:

* Database accounts used to restore SQL databases must have the following server-level roles assigned: ##MS\_DatabaseManager##, ##MS\_LoginManager##, ##MS\_DatabaseConnector## and ##MS\_DefinitionReader##. However, consider that you cannot use database accounts having the db\_owner database-level role to restore SQL databases. For more information on [server-level roles](https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver16) and [database-level roles](https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/database-level-roles?view=sql-server-ver16), see Microsoft Docs.

Cosmos DB Restore

When restoring Cosmos DB accounts, consider the following:

* Database accounts used to restore Cosmos DB for PostgreSQL accounts must have any role that has administrative permissions assigned; it is recommended that you use an account that has the built-in citus role assigned. For more information on native PostgreSQL roles, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/cosmos-db/postgresql/how-to-configure-authentication?tabs=portal).

Azure Files Restore

When restoring Azure file shares, consider the following:

* File-level recovery is supported for the following file systems only: FAT, FAT32, NTFS, ext2, ext3, ext4, XFS, Btrfs.
* For Microsoft Windows systems, Veeam Plug-in for Microsoft Azure supports file-level recovery for Microsoft Windows basic volumes only. If you use Windows Storage Spaces to store data, restore an [entire Azure VM](azure_entire_vm_restore_ui.md) to get access to your files and folders. For more information on Storage Spaces, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/overview).
* Veeam Backup for Microsoft Azure does not support file-level recovery to the original location for files and folders of Arm-based Azure VMs. For more information on Arm-based Azure VMs, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows/arm/create-arm-vm).

* Veeam Plug-in for Microsoft Azure does not support file-level recovery for volumes with Windows-native Data Deduplication enabled. For more information on the deduplication feature, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/overview).

Immutability

Consider that you cannot perform the following operations with image-level backups and archived backups stored in repositories with [immutability](azure_immutability.md) enabled:

* You cannot remove data manually using the Veeam Backup for Microsoft Azure Web UI, as described in sections [Removing VM Backups and Snapshots](azure_removing_vm_backups_and_snapshots.md), [Removing SQL Backups](azure_removing_sql_backups.md), [Removing Cosmos DB Backups](azure_removing_cosmos_db_backups.md) and [Removing Virtual Network Configuration Backups](azure_removing_vnet_backups.md) — until the immutability period is over.
* You can neither remove data from Microsoft Azure using any cloud service provider tools nor request the technical support department to do it for you — none of the protected objects can be overwritten or deleted by any user, including the Global Administrator in your Microsoft Entra ID.

Azure Disk Encryption

Azure Disk Encryption is supported with the following limitations:

* Backup and restore operations are supported within one Azure region only. If you choose to back up or restore your data to another region, you must first migrate to the target region all Azure key vaults, cryptographic keys and secrets used to encrypt the source Azure resources, as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/key-vault/general/move-region).
* File-level recovery is not supported for VMs whose virtual disks are encrypted using Azure Disk Encryption. That is, you cannot restore and browse guest OS files on disks encrypted by BitLocker for Windows-based Azure VMs, by DM-Crypt for Linux-based Azure VMs, as well as by any custom disk encryption tools.

For more information on Azure Disk Encryption, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/security/fundamentals/encryption-overview).

SureBackup

Starting from version 8.1, Veeam Backup for Microsoft Azure supports the SureBackup functionality for backup appliances managed by Veeam Backup & Replication servers. However, this functionality is limited at the moment — you can perform backup verification and content scan only. Also, consider that since SureBackup performs backup integrity check and extensive content analysis, it requires additional data to be read from Microsoft Azure, which may incur an increase in the associated costs.

For more information on SureBackup, see [Recovery Verification](surebackup_hiw.md).

Page updated 2026-07-17

