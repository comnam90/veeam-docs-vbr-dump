---
title: "Add-VBRBackupRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrbackuprepository.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRBackupRepository

In this article

Short Description

Adds a backup repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a repository without authentication.

|  |
| --- |
| Add-VBRBackupRepository -Folder <string> -Type {WinLocal | LinuxLocal | CifsShare | ExaGrid | DataDomain |HPStoreOnceIntegration | Quantum | Nfs | Infinidat | Fujitsu | HPStoreOnceCloudBank | Hardened} [-Name <string>] [-Description <string>] [-Server <CHost[]>] [-AutoSelectGateway] [-MountServer <CHost>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-ImportIndex] [-ImportBackup] [-RotatedDrive] [-RotatedDriveCleanupMode {ContinueBackupChain | ClearBackupFolder | ClearRepositoryFolder}] [-MountFolder <string>] [-VPowerNFSPort <int>] [-MountPort <int>] [-DDServerName <string>] [-StoreOnceServerName <string>] [-StoreOnceWanLink] [-LimitConcurrentJobs] [-MaxConcurrentJobs <int>] [-LimitDatarate] [-DataRateLimit <int>] [-AlignDataBlocks] [-DecompressDataBlocks] [-UsePerVMFile] [-DDBoostEncryptionType {None | Medium | High}] [-EnableXFSFastClone] [-EnableReFSFastClone] [-EnableBackupImmutability] [-ImmutabilityPeriod <int>] [-NFSRepositoryEncoding {utf | ansi}] [-Force]  [<CommonParameters>] |

* Add a repository with a user name and password.

|  |
| --- |
| Add-VBRBackupRepository -Folder <string> -Type {WinLocal | LinuxLocal | CifsShare | ExaGrid | DataDomain |HPStoreOnceIntegration | Quantum | Nfs | Infinidat | Fujitsu | HPStoreOnceCloudBank | Hardened} [-Name <string>] [-Description <string>] [-Server <CHost[]>] [-AutoSelectGateway] [-MountServer <CHost>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-ImportIndex] [-ImportBackup] [-RotatedDrive] [-RotatedDriveCleanupMode {ContinueBackupChain | ClearBackupFolder | ClearRepositoryFolder}] [-MountFolder <string>] [-VPowerNFSPort <int>] [-MountPort <int>] [-DDServerName <string>] [-StoreOnceServerName <string>] [-StoreOnceWanLink] [-UserName <string>] [-Password <string>] [-LimitConcurrentJobs] [-MaxConcurrentJobs <int>] [-LimitDatarate] [-DataRateLimit <int>] [-AlignDataBlocks] [-DecompressDataBlocks] [-UsePerVMFile] [-DDBoostEncryptionType {None | Medium | High}] [-EnableXFSFastClone] [-EnableReFSFastClone] [-EnableBackupImmutability] [-ImmutabilityPeriod <int>] [-NFSRepositoryEncoding {utf | ansi}] [-Force]  [<CommonParameters>] |

* Add a repository using credentials.

|  |
| --- |
| Add-VBRBackupRepository -Folder <string> -Type {WinLocal | LinuxLocal | CifsShare | ExaGrid | DataDomain |HPStoreOnceIntegration | Quantum | Nfs | Infinidat | Fujitsu | HPStoreOnceCloudBank | Hardened} [-Name <string>] [-Description <string>] [-Server <CHost[]>] [-AutoSelectGateway] [-MountServer <CHost>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-ImportIndex] [-ImportBackup] [-RotatedDrive] [-RotatedDriveCleanupMode {ContinueBackupChain | ClearBackupFolder | ClearRepositoryFolder}] [-MountFolder <string>] [-VPowerNFSPort <int>] [-MountPort <int>] [-DDServerName <string>] [-StoreOnceServerName <string>] [-StoreOnceWanLink] [-Credentials <CCredentials>] [-LimitConcurrentJobs] [-MaxConcurrentJobs <int>] [-LimitDatarate] [-DataRateLimit <int>] [-AlignDataBlocks] [-DecompressDataBlocks] [-UsePerVMFile] [-DDBoostEncryptionType {None | Medium | High}] [-EnableXFSFastClone] [-EnableReFSFastClone] [-EnableBackupImmutability] [-ImmutabilityPeriod <int>] [-NFSRepositoryEncoding {utf | ansi}] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a new backup repository to the backup infrastructure.

To add a scale-out backup repository, run the [Add-VBRScaleOutBackupRepository](add-vbrscaleoutbackuprepository.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Folder | Specifies the full path to the folder where you want to store the backups. | String | True | Named | False |
| Type | Specifies the type you want to assign to the repository:   * WinLocal * LinuxLocal * CifsShare * ExaGrid * DataDomain * HPStoreOnceIntegration * Quantum * Nfs * Infinidat * Fujitsu * HPStoreOnceCloudBank * Hardened | VBRRepositoryType | True | Named | False |
| ImmutabilityPeriod | For the immutability option.  Defines a number of days within which Veeam Backup & Replication will not delete blocks of data from the backup repository.  Default: 30 days. | Int | False | Named | False |
| EnableBackupImmutability | Enables the immutability option for a backup repository.  Default: False. | SwitchParameter | False | Named | False |
| NFSRepositoryEncoding | Specifies encoding for NFS share. You can specify either of the following values:   * utf * ansi | VBRNASEncoding | False | Named | False |
| Force | Defines that the cmdlet will add a backup repository without showing warnings in the PowerShell console.  Default: False. | SwitchParameter | False | Named | False |
| Name | Specifies the name you want to assign to the new backup repository. | String | False | Named | False |
| Description | Specifies the description of the backup repository. | String | False | Named | False |
| Server | Specifies the host where the backup repository you want to add is located and host that will be used as gateway servers.  Use this parameter to explicitly set the host for the following repository types:   * WinLocal: to specify a Windows based server where you want to create the backup repository or to which you want to connect the rotated drives. * LinuxLocal type: to specify a Linux based server where you want to create the backup repository or to which you want to connect the rotated drives.   Note: when you specify an array of hosts, the first host is used as a backup repository, the others are used as gateway servers.   * CifsShare, DataDomain or HPStoreOnce: to specify a Windows based server to which the storage appliance is connected and which will be used as a gateway server.   Default: This server. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| AutoSelectGateway | Enables automatic selection of gateway servers.  Default: False. | SwitchParameter | False | Named | False |
| MountServer | Specifies the mount server associated with the backup repository. You can assign the mount server role to the backup repository itself or to a server that resides close to the backup repository. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| MountServerOptions | Specifies the mount server settings for the servers that you plan to use as mount servers during the restore process. | Accepts the VBRRepositoryMountServerOptions[] object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| ImportIndex | Defines that the cmdlet will import the guest OS file system index.  Default: False. | SwitchParameter | False | Named | False |
| ImportBackup | Defines that the cmdlet will import backups that are currently located on the server you are adding as repository.  Default: False. | SwitchParameter | False | Named | False |
| RotatedDrive | Defines that the repository you want to add is a rotated drive (removable media).  Default: False. | SwitchParameter | False | Named | False |
| RotatedDriveCleanupMode | Defines how Veeam Backup & Replication behaves when a drive is swapped:   * ContinueBackupChain: use this option to continue the backup chain. * ClearBackupFolder: use this option to delete all backups created by a job. * ClearRepositoryFolder: use this option to delete all backups stored in the repository folder (for example, C:\Backups\). Note that Veeam Backup & Replication will delete all backups, even backups created by other jobs.   Default: ContinueBackupChain. | VBRRotatedDriveCleanupMode | False | Named | False |
| MountFolder | Specifies the path to the mount folder. Veeam Backup & Replication will use this folder to mount VM disks and to keep write cache data. | String | False | Named | False |
| VPowerNFSPort | Specifies the port number of the vPower NFS Service. Veeam Backup & Replication will set up a direct connection between the backup repository and ESXi to which the vPower NFS datastore is mounted.  Default: 2049. | Int | False | Named | False |
| MountPort | Specifies the port number of the mount server.  Default: 1058. | Int | False | Named | False |
| DDServerName | Specifies the Data Domain server name. Enter the name in the following formats depending on the connection mode:   * If Dell Data Domain works over TCP/IP, enter a full DNS name or an IP address of the Dell Data Domain server. * If Dell Data Domain works over Fibre Channel, enter a name of the Data Domain server starting with the 'DFC-' prefix, for example, DFC-DataDomain690. | String | False | Named | False |
| StoreOnceServerName | Specifies the HPE StoreOnce server name. | String | False | Named | False |
| StoreOnceWanLink | Defines that the HPE StoreOnce must use source-side deduplication.  Default: False. | SwitchParameter | False | Named | False |
| LimitConcurrentJobs | Defines that the number of concurrent jobs using this repository must be limited.  Use the MaxConcurrentJobs parameter to set the maximum value.  Default: True. | SwitchParameter | False | Named | False |
| MaxConcurrentJobs | Used for setting maximum value for the LimitConcurrentJobs parameter.  Specifies the maximum allowed number of concurrent tasks for the backup repository.  Permitted values: 1 to 128.  Permitted values for Dell Data Domain: 1 to 270. | Int | False | Named | False |
| LimitDatarate | Defines that the total speed of writing data to the backup repository disk must be restricted.  Use the DataRateLimit parameter to set the maximum value.  Default: False. | SwitchParameter | False | Named | False |
| DataRateLimit | Used for setting combined data ingestion rate for the LimitDatarate parameter.  Specifies the combined data ingestion rate for the repository.  Permitted value: 1 to 1024 (MByte/s). | Int | False | Named | False |
| AlignDataBlocks | Defines that the backup blocks size will be aligned by a 4Kb block boundary. Data alignment provides better deduplication on storage systems with fixed block size.  Default: False. | SwitchParameter | False | Named | False |
| DecompressDataBlocks | Defines that the backup data blocks must be decompressed before storing to the repository.  Default: False. | SwitchParameter | False | Named | False |
| UsePerVMFile | This parameter is obsolete and is not supported.  Note: Backup repositories always create per-VM backup files. | SwitchParameter | False | Named | False |
| DDBoostEncryptionType | Specifies the native Dell Data Domain encryption level:   * High * Medium * None | VBRDDBoostEncryptionType | False | Named | False |
| UserName | Specifies the user name you want to use for authenticating with the backup repository host. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the backup repository host. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the backup repository host. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| EnableXFSFastClone | Enables the Fast Clone technology for the backup repository.  Default: False. | SwitchParameter | False | Named | False |
| EnableReFSFastClone | Enables the ReFS Fast Clone technology for SMB backup repositories. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupRepository object that contains settings of backup repositories added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Windows Server as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add the Win2012 Windows server as a new backup repository named Win2012Repo. The cmdlet will add the backup repository with the following settings:   * Veeam Backup & Replication does not authenticate against the Win2012 Windows server.  * The folder that is used as the backup repository is located on C:\Backup Repository. * The server type is set to WinLocal.     |  | | --- | | $server = Get-VBRServer -Name "Win2012"  Add-VBRBackupRepository -Name "Win2012Repo" -Server $server -Folder "c:\Backup Repository" -Type WinLocal |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $server variable as the Server parameter value. * Specify the Folder parameter value. * Specify the Type parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Linux Server as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add a Linux server as a backup repository. Veeam Backup & Replication will store backup files in the folder located in the following path: /home/Admin/backups.  |  | | --- | | $linsrv = Add-VBRLinux -Name "172.18.4.67" -SSHUser Admin -SSHPassword P@$$w0rd  Add-VBRBackupRepository -Name "Linux Repository" -Server $linsrv -Type LinuxLocal -Folder "/home/Admin/backups/" |  Perform the following steps:   1. Run the [Add-VBRLinux](add-vbrlinux.md) cmdlet. Specify the Name, SSHUser and SSHPassword parameter values. Save the result to the $linsrv variable. 2. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $linsrv variable as the Server parameter value.  * Set the LinuxLocal option for the Type parameter.  * Specify the Folder parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Linux Server with Hardened Repository Role

|  |  |
| --- | --- |
| This example shows how to add the 198.51.100.5 Linux server as a hardened repository. The cmdlet will add the backup repository with the following settings:   * The Linux server is added with temporary elevate to root and failover to su single-use credentials. * Veeam Backup & Replication will store backup files in the folder located in the following path: /home/Admin/backups. * Immutability period is set to 21 days.   |  | | --- | | $linsrv = Add-VBRLinux -Name "198.51.100.5" -SSHUser "User" -SSHPassword "qwerty" -SSHElevateToRoot -SSHTempCredentials -SSHFailoverToSu -SSHRootPassword "passcode"  Add-VBRBackupRepository -Folder "/home/Admin/backups/" -Type Hardened -Name "Hardened Repository" -Server $linsrv -EnableBackupImmutability -ImmutabilityPeriod 21 |  Perform the following steps:   1. Run the [Add-VBRLinux](add-vbrlinux.md) cmdlet. Specify the necessary parameters. Save the result to the $linsrv variable. 2. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Folder parameter value.  * Set the Hardened option for the Type parameter.  * Specify the Name parameter value. * Set the $linsrv variable as the Server parameter value. * Provide the EnableBackupImmutability parameter. * Specify the ImmutabilityPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Adding SMB (CIFS) Shared Folder as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add an SMB (CIFS) shared folder on a Windows server as the Backups Vol 01 backup repository. The cmdlet will add the backup repository with the following settings:   * Veeam Backup & Replication uses credentials to authenticate against the shared folder.  * The server type is set to CifsShare.  * The \\nimble\Backups folder is used as the backup repository. * The same server is used as a mount server. * The ImportBackup parameter is set to import the existing backup files. * The maximum allowed number of concurrent tasks is set to 6.     |  | | --- | | $server = Get-VBRServer -Name "TestServer05"  $mountserver = Get-VBRServer -Name "TestServer05"  $administrator = Get-VBRCredentials -Name "Administrator"  Add-VBRBackupRepository -Type CifsShare -Name "Nimble Script Share" -Server $server -Folder "\\nimble\Backups" -MountServer $mountserver -ImportBackup:$true -LimitConcurrentJobs -MaxConcurrentJobs 6 -Credentials $administrator |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $mountserver variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $administrator variable. 4. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Set the CifsShare option for the Type parameter. * Specify the Name parameter value. * Set the $server variable as the Server parameter value. * Specify the Folder parameter value. * Set the $mountserver variable as the MountServer parameter value. * Set the ImportBackup parameter to $true. * Provide the LimitConcurrentJobs parameter. * Specify the MaxConcurrentJobs parameter value. * Set the $administrator variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Adding Dedupe Storage Appliance as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add a Dell Data Domain storage appliance as a backup repository. The cmdlet will add the backup repository with the following settings:   * Dell Data Domain connects to the WinSrv05 explicitly set as a gateway server. * The DFC prefix is not set to allow Veeam Backup & Replication to communicate with Dell Data Domain storage over the TCP/IP protocol.  * Veeam Backup & Replication will store backup files in the folder located in the following path: ddboost://10.0.0.80:storage/. * The Username/Password is used to get access to the appliance.     |  | | --- | | $server = Get-VBRServer -Name "WinSrv05"  Add-VBRBackupRepository -Folder ddboost://10.0.0.80:storage/ -Type DataDomain -DDServerName 10.0.0.80 -Server $server -UserName sysadmin -Password Pa55word |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Folder parameter value.  * Specify the Type parameter value.  * Specify the DDServerName parameter value. * Set the $server variable as the Server parameter value. * Specify the UserName parameter value. * Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Adding Backup Repository on Rotated Drive

|  |  |
| --- | --- |
| This example shows how to add backup repository on a rotated drive connected to a Windows server. The cmdlet will add the backup repository with the following settings:   * The server type is set to WinLocal. * Veeam Backup & Replication will store backup files in the folder located in the following path: F:\Repo.       |  | | --- | | $server = Get-VBRServer -Name "WinSrv05"  Add-VBRBackupRepository -Name RDX -Type WinLocal -RotatedDrive -Description "Rotated drive" -Server $server -Folder F:\Repo |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Name parameter value.  * Set the WinLocal option for the Type parameter value. * Provide the RotatedDrive parameter.  * Specify the Description parameter value. * Set the $server variable as the Server parameter value.  * Specify the Folder parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Adding Quantum DXi Storage Appliance as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add a Quantum DXi storage appliance as a backup repository. Veeam Backup & Replication will store backup files in the folder located in the following path: /shares/Quantum-Share-01.  |  | | --- | | $server = Get-VBRServer -Name "WinSrv05"  Add-VBRBackupRepository -Name "Quantum DXi" -Type Quantum -Folder "/shares/Quantum-Share-01" -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Name parameter value.  * Set the Quantum option for the Type parameter.  * Specify the Folder parameter value.  * Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 8. Adding ExaGrid Share as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add ExaGrid as a backup repository. Veeam Backup & Replication will store backup files in the folder located in the following path: /home/Admin/Share01-07/MyRepo. The pattern of this folder path consists of the following elements:   1. /home: A home directory. 2. /Admin: Must be the same as the user name that you use to authenticate against the Linux server when you add it to Veeam Backup & Replication. In our example it is specified by the SSHUser parameter of the [Add-VBRLinux](add-vbrlinux.md) cmdlet. 3. /Share01-07: The folder that you must create on the Exagrid appliances beforehand. 4. [Optional] /MyRepo/: Subfolder that you may want to create in the Share01-07 folder.   |  | | --- | | $srv = Add-VBRLinux -Name "172.18.4.67" -SSHUser Admin -SSHPassword P@$$w0rd  Add-VBRBackupRepository -Name ExaGrid -Server $srv -Type ExaGrid -Folder "/home/Admin/Share01-07/MyRepo/" |  Perform the following steps:   1. Run the [Add-VBRLinux](add-vbrlinux.md) cmdlet. Specify the Name, SSHUser and SSHPassword parameter values. Save the result to the $srv variable. 2. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $srv variable as the Server parameter value.  * Set the ExaGrid option for the Type parameter.  * Specify the Folder parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 9. Adding HPE StoreOnce as Backup Repository

|  |  |
| --- | --- |
| This example shows how to add HPE StoreOnce as a backup repository. Veeam Backup & Replication will store backup files in the folder located in the following path: storeonce://HPEStoreO01-dl.local:Store-015/. The pattern of this folder path consists of the following elements:   1. //HPEStoreO01-dl.local: The name of HPE StoreOnce. 2. :Store-015@/: The name of the HPE StoreOnce Catalyst Store.   Note: It is not recommended to specify any subfolders in this folder, since currently Veeam Backup & Replication is able to display only the name of HPE StoreOnce Catalyst Store. If you indeed want to specify a subfolder, review this [KB article](https://www.veeam.com/kb2987) but keep in mind that you will not be able to manage the backup repository with the user interface of Veeam Backup & Replication.  |  | | --- | | $creds = Get-VBRCredentials -Name "HPEStorOnce"  Add-VBRBackupRepository -Type HPStoreOnceIntegration -Name "Atlanta Repository" -StoreOnceServerName "HPEStoreO01-dl.local" -Folder "storeonce://HPEStoreO01-dl.local:Store-015@/" -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 2. Run the Add-VBRBackupRepository cmdlet. Specify the following settings:  * Set the HPStoreOnceIntegration option for the Type parameter. * Specify the Name parameter value. * Specify the StoreOnceServerName parameter value. * Specify the Folder parameter value. * Set the $creds variable as the Credentials parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Add-VBRLinux](add-vbrlinux.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
