---
title: "Set-VBRBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrbackuprepository.html"
last_updated: "1/21/2026"
product_version: "13.0.1.1071"
---

# Set-VBRBackupRepository


Short Description

Modifies a backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRBackupRepository -Repository <CBackupRepository> [-Name <string>] [-Description <string>] [-MountServer <CHost>] [-Server <CHost[]>] [-AutoSelectGateway] [-RotatedDrive] [-RotatedDriveCleanupMode {ContinueBackupChain | ClearBackupFolder | ClearRepositoryFolder}] [-EnableVPowerNFS] [-VPowerNFSPort <int>] [-MountPort <int>] [-MountFolder <string>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-DDServerName <string>] [-RequireAccessCreds] [-Credentials <CCredentials>] [-LimitConcurrentJobs] [-MaxConcurrentJobs <int>] [-LimitDatarate] [-DataRateLimit <int>] [-AlignDataBlocks] [-DecompressDataBlocks] [-UsePerVMFile] [-DDBoostEncryptionType {None | Medium | High}] [-AffinityMode {Auto | Manual}] [-AffinityProxy <CViProxy[]>] [-EnableXFSFastClone] [-EnableReFSFastClone] [-EnableBackupImmutability] [-ImmutabilityPeriod <int>] [-NFSRepositoryEncoding {utf | ansi}] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a backup repository.

To modify a scale-out backup repository, run the [Set-VBRScaleOutBackupRepository](set-vbrscaleoutbackuprepository.md) cmdlet.

To modify an object storage backup repository, use cmdlets from the [Object Storage Repositories](object_storage_repositories.md) section.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the backup repository you want to modify. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the backup repository. | String | False | Named | False |
| Description | Specifies the description of the backup repository. | String | False | Named | False |
| Server | Specifies the array of hosts where the backup repositories are located. The cmdlet will set this host as a backup repository.  Default: This server.  Note: You can not set a new backup repository for the following types of hosts that have been added as backup repositories:   * WinLocal * LinuxLocal | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| AutoSelectGateway | Enables automatic selection of gateway servers.  Default: False. | SwitchParameter | False | Named | False |
| ImmutabilityPeriod | For the immutability option.  Defines a number of days within which Veeam Backup & Replication will not delete blocks of data from the backup repository.  Default: 30 days. | Int32 | False | Named | False |
| EnableBackupImmutability | Enables the immutability option for a backup repository.  Default: False. | SwitchParameter | False | Named | False |
| NFSRepositoryEncoding | Specifies encoding for NFS share. You can specify either of the following values:   * utf * ansi | VBRNASEncoding | False | Named | False |
| Force | Defines that the cmdlet will modify backup repository without showing warnings in the PowerShell console.  Default: False. | SwitchParameter | False | Named | False |
| MountFolder | Specifies the path to the mount folder. Veeam Backup & Replication will use this folder to mount VM disks  and to keep write cache data. | String | False | Named | False |
| MountServer | Specifies the mount server associated with the backup repository. You can assign the mount server role to the backup repository itself or to a server that resides close to the backup repository. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| RotatedDrive | Defines that the repository you want to add is a rotated drive (removable media).  Default: False. | SwitchParameter | False | Named | False |
| RotatedDriveCleanupMode | Defines how Veeam Backup & Replication behaves when a drive is swapped:   * ContinueBackupChain: use this option to continue the backup chain. * ClearBackupFolder: use this option to delete all backups created by a job. * ClearRepositoryFolder: use this option to delete all backups stored in the repository folder (for example, C:\Backups\). Note that Veeam Backup & Replication will delete all backups, even backups created by other jobs.   Default: ContinueBackupChain. | VBRRotatedDriveCleanupMode | False | Named | False |
| EnableVPowerNFS | Enables the repository to be accessible by the vPower NFS service.  Default: False. | SwitchParameter | False | Named | False |
| VPowerNFSPort | Specifies the port number of the vPower NFS Service. Veeam Backup & Replication will set up a direct connection between the backup repository and ESXi to which the vPower NFS datastore is mounted.  Default: 2049. | Int32 | False | Named | False |
| MountPort | Specifies the port number of the mount server.  Default: 1058. | Int32 | False | Named | False |
| RequireAccessCreds | Defines that the administrator credentials are needed to access the shared folder. Use the Credentials parameter to specify the credentials.  Default: False. | SwitchParameter | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the backup repository host. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| LimitConcurrentJobs | Defines that the number of concurrent jobs using this repository must be limited. Use the MaxConcurrentJobs parameter to set the maximum value. | SwitchParameter | False | Named | False |
| MaxConcurrentJobs | Used for setting maximum value for the LimitConcurrentJobs parameter.  Specifies the maximum allowed number of concurrent tasks for the backup repository.  Permitted values: 1 to 128. | Int32 | False | Named | False |
| LimitDatarate | Defines that the total speed of writing data to the backup repository disk must be restricted. Use the DataRateLimit parameter to set the maximum value.  Default: False. | SwitchParameter | False | Named | False |
| DataRateLimit | Used for setting combined data ingestion rate for the LimitDatarate parameter.  Specifies the combined data ingestion rate for the repository.  Permitted value: 1 to 1024 (MByte/s). | Int32 | False | Named | False |
| AlignDataBlocks | Defines that the backup blocks size will be aligned by a 4Kb block boundary. Data alignment provides better deduplication on storage systems with fixed block size.  Default: False. | SwitchParameter | False | Named | False |
| DecompressDataBlocks | Defines that the backup data blocks must be decompressed before storing to the repository. | SwitchParameter | False | Named | False |
| UsePerVMFile | This parameter is obsolete and is not supported.  Note: Backup repositories always create per-VM backup files. | SwitchParameter | False | Named | False |
| DDBoostEncryptionType | Specifies the native Dell Data Domain encryption level:   * High * Medium * None | VBRDDBoostEncryptionType | False | Named | False |
| AffinityMode | Specifies what proxy affinity rules are set up for the backup repository:   * Auto — use this option if you want all backup proxies in the backup infrastructure to work with the backup repository. * Manual — use this option if you want backup proxies from the AffinityProxy list to work with the backup repository.   To configure proxy affinity settings, you must install Veeam Backup & Replication Enterprise or higher license on the backup server.  Default: Auto. | VBRProxyAffinityMode | False | Named | False |
| AffinityProxy | Specifies the list of backup proxies that can work with the backup repository. Entries in the proxy affinity list are separated with a comma.  To configure proxy affinity settings, you must install Veeam Backup & Replication Enterprise or higher license on the backup server. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| EnableXFSFastClone | Enables the Fast Clone technology for the backup repository.  Default: False. | SwitchParameter | False | Named | False |
| EnableReFSFastClone | Enables the ReFS Fast Clone technology for SMB backup repositories. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupRepository object that contains settings of backup repositories added to the backup infrastructure.

Examples

Defining Proxy Affinity Settings

This example shows how to configure proxy affinity settings for the backup repository named Backup Volume 01.

|  |
| --- |
| $repository = Get-VBRBackupRepository -Name "Backup Volume 01"  $proxy01 = Get-VBRViProxy -Name 172.17.53.5  $proxy02 = Get-VBRViProxy -Name 172.17.53.33  Set-VBRBackupRepository -Repository $repository -AffinityMode Manual -AffinityProxy $proxy01, $proxy02 |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy01 variable.
3. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy02 variable.
4. Run the Set-VBRBackupRepository cmdlet. Set the $repository variable as the Repository parameter value. Set the Manual option for the AffinityMode parameter. Set the $proxy01 and $proxy02 variables as the AffinityProxy parameter values.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)


