---
title: "Add-VBRCDPPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcdppolicy.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCDPPolicy


Short Description

Creates CDP policies for VMware vSphere VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a CDP policy that replicates VMs to a cluster.

|  |
| --- |
| Add-VBRCDPPolicy -Entity <IViItem[]> -TargetCluster <CViClusterItem> [-Exclusions <IViItem[]>] [-Name <string>] [-Description <string>] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-ReIpRule <IViReIpRule[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy <VBRCDPProxy[]>] [-Suffix <string>] [-CompressionLevel <VBRCompressionLevel> {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-RepositorySeed <CBackupRepository>] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <CViVmItem[]>] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-DiskType <EDiskCreationMode>]  [<CommonParameters>] |

* Create a CDP policy that replicates VMs on an ESXi host.

|  |
| --- |
| Add-VBRCDPPolicy -Entity <IViItem[]> -TargetHost <CEsxItem> [-Exclusions <IViItem[]>] [-Name <string>] [-Description <string>] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-ReIpRule <IViReIpRule[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy<VBRCDPProxy[]>] [-Suffix <string>] [-CompressionLevel <VBRCompressionLevel> {None | DedupeFriendly | Optimal |High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-RepositorySeed <CBackupRepository>] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <CViVmItem[]>] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-DiskType <EDiskCreationMode>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates CDP policies.

|  |
| --- |
| Note |
| The cmdlet will create a CDP policy in the disabled state unless you enable a policy schedule. Run the [Enable-VBRCDPPolicy](enable-vbrcdppolicy.md) cmdlet to enable the policy. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies an array of VMs that you want to add to a CDP policy. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| TargetCluster | Specifies a target cluster. The cmdlet will replicate VMs to this cluster. | Accepts the CViClusterItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| TargetHost | Specifies a target ESXi host. The cmdlet will replicate VMs to this ESXi host. | Accepts the CEsxItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| Exclusions | Specifies an array of VMs that you want to exclude from a CDP policy processing. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Name | Specifies a name for a CDP policy. | String | False | Named | False |
| Description | Specifies a description for a CDP policy. | String | False | Named | False |
| ResourcePool | Specifies the resource pool to which you want to replicate VMs. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder to which you want to replicate VMs. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Datastore | Specifies the datastore to which you want to replicate VMs. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy that must be applied to the replica virtual disks. | Accepts the VBRViStoragePolicy object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| SourceNetwork | For network mapping.  Specifies an array of production networks to which the VMs added to a CDP policy are connected.  Note: The number of source networks must match the number of target networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For network mapping.  Specifies an array of networks in the disaster recovery site. VMs that are replicated with the CDP policy will be connected to these networks.  Note: The number of source networks must match the number of target networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| ReIpRule | Specifies re-IP rules. | Accepts the VBRViReplicaReIpRule or VBRViReplicaReIpIPv6Rule object. To get this object, run the [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the proxy in the production site that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the target proxy that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of VMs replicated with CDP policies.  Default: "\_replica". | String | False | Named | False |
| CompressionLevel | Specifies the compression level of the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | VBRCompressionLevel | False | Named | False |
| NotificationOptions | Specifies notification settings of a CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings of a CDP policy. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository that keeps a full backup of VMs that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVM | For replica mapping.  Specifies an array of production VMs that you want to replicate using replica mapping.  The CDP policy will map this VM to the VM in the disaster recovery site.  Use the ReplicaVM parameter to specify the replicated VM on the disaster recovery site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies an array VM on the disaster recovery site. The cmdlet will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| GuestProcessingOptions | Specifies guest processing settings of a CDP policy. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| DiskType | Specifies the type of disks for replicas:   * Source: the restored replica disks will be the same format as source. * Thick: the restored replica disks will be thick. * Thin: the restored replica disks will be thin.  * ThickEagerZeroed: the restored replica disks will be thick eager zeroed. | EDiskCreationMode | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPPolicy object that defines settings of a CDP policy.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating CDP Policy that Replicates VM to Cluster

|  |  |
| --- | --- |
| This example shows how to create the SQL09 CDP policy that will replicate the WinSrv05 VM to the CDP cluster. The description of the policy is set to Microsoft SQL database replica.  |  | | --- | | $vm = Find-VBRViEntity -Name "WinSrv05"  $cluster = Find-VBRViEntity -Name "CDP"  Add-VBRCDPPolicy -Entity $vm -TargetCluster $cluster -Name "SQL09" -Description "Microsoft SQL database replica" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $cluster variable. 3. Run the Add-VBRCDPPolicy cmdlet. Set the $vm variable as the Entity parameter value. Set the $cluster variable as the TargetCluster parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating CDP Policy that Replicates VM to ESXi Host

|  |  |
| --- | --- |
| This example shows how to create the DevOps61021 CDP policy that will replicate the DevOps Production VM to the esx05.tech.local VMware host. The description of the policy is set to DevOpsVM replica.  |  | | --- | | $vm = Find-VBRViEntity -Name "DevOps Production"  $host = Find-VBRViEntity -Name "esx05.tech.local"  Add-VBRCDPPolicy -Entity $vm -TargetHost $host -Name "DevOps61021" -Description "DevOpsVM replica" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 3. Run the Add-VBRCDPPolicy cmdlet. Specify the following settings:  * Set the $vm variable as the Entity parameter value. * Set the $host variable as the TargetHost parameter value. * Specify the Name parameter value. * Specify the Description parameter value. |

Related Commands

[Find-VBRViEntity](find-vbrvientity.md)


