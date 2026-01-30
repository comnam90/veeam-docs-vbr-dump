---
title: "Set-VBRvCDCloudCDPPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcdcloudcdppolicy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Set-VBRvCDCloudCDPPolicy


Short Description

Modifies a VDC CDP policy.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCDCloudCDPPolicy -Policy <VBRvCDCloudCDPPolicy> [-Entity <IViItem[]>] [-OrganizationvDC <VBRvCDCloudOrganizationvDC>] [-vApp <VBRvCDCloudvApp>] [-Name <String>] [-Description <String>] [-Suffix <String>] [-StoragePolicy <VBRvCDCloudStoragePolicy>] [-SourceProxy <VBRCDPProxy[]>] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-EnableApplicationProcessingOptions] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRvCDCloudNetworkInfo[]>] [-EnableReplicaSeeding] [-RepositorySeed <CBackupRepository>] [-EnableReplicaMapping] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <VBRvCDCloudVM[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a VDC CDP policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies a cloud CDP policy that you want to modify. | Accepts the VBRCloudCDPPolicy object. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Entity | Specifies the array of VMs you want to add to a VDC CDP policy. | Accepts the IViItem[] object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| OrganizationvDC | Specifies the cloud organization VDC. The VDC CDP policy will store replicas in the selected organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | False | Named | False |
| vApp | Specifies the vApp container. The VDC CDP policy will store the replicas in the selected container.  Note: If you do not specify the vApp container, the job will store the replicas in the default vApp. | Accepts the VBRvCDCloudvApp object. To get this object, run the [Get-VBRvCDCloudvApp](get-vbrvcdcloudvapp.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the Cloud Director storage policy. The VDC CDP policy will create replicas according to this storage policy settings. | Accepts the VBRvCDCloudStoragePolicy object. To get this object, run the [Get-VBRvCDCloudStoragePolicy](get-vbrvcdcloudstoragepolicy.md) cmdlet. | False | Named | False |
| Name | Specifies a name you want to assign to a VDC CDP policy. | String | False | Named | False |
| Description | Specifies a description of a VDC CDP policy. | String | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Note: If you omit this parameter, the replicated VMs will get the '\_replica' suffix. | String | False | Named | False |
| SourceProxy | Used for building a replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  Note: You cannot specify a cloud repository. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings of a VDC CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings of a VDC CDP policy. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |
| EnableApplicationProcessingOptions | Enables guest processing options for a VDC CDP policy.  Use the GuestProcessingOptions parameter to specify the guest processing settings. | SwitchParameter | False | Named | False |
| GuestProcessingOptions | Specifies guest processing options of a VDC CDP policy. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| EnableNetworkMapping | Enables network mapping.  To set the network mapping rules, use the following parameters:   * SourceNetwork * TargetNetwork | SwitchParameter | False | Named | False |
| SourceNetwork | For network mapping.  Specifies an array of production networks to which the VMs added to a VDC CDP policy are connected.  Note: The number of source networks must match the number of target networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For network mapping.  Specifies an array of networks in the disaster recovery site. VMs that are replicated with the VDC CDP policy will be connected to these networks.  Note: The number of source networks must match the number of target networks. | Accepts the VBRvCDCloudNetworkInfo[] object. To get this object, run the [Get-VBRvCDCloudNetworkInfo](get-vbrvcdcloudnetworkinfo.md) cmdlet. | False | Named | False |
| EnableReplicaSeeding | Enables replica seeding.  To specify replica seeding repository settings, use the RepositorySeed parameter. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies a backup repository that keeps a full backup of VMs that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReplicaMapping | Enables replica mapping. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies an array of production VMs that you want to replicate using replica mapping.  The VDC CDP policy will map this VM to the VM in the disaster recovery site.  Use the ReplicaVM parameter to specify the replicated VM on the disaster recovery site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies an array VM in the disaster recovery site. The cmdlet will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the VBRvCDCloudVM[] object. To get this object, run the [Get-VBRvCDCloudVM](get-vbrvcdcloudvm.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a VDC CDP policy without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDCloudCDPPolicy object that contains Cloud Director CDP policy settings.

Examples

Modifying Source Proxies for Cloud Director CDP Policy

This example shows how to change the CDP source proxies for the DB\_replication Cloud Director CDP policy. The cmdlet will set the Proxy\_05 to transfer the replica data.

|  |
| --- |
| $policy = Get-VBRCDPPolicy -Name "DB\_replication"  $proxy = Get-VBRCDPProxy -Name "Proxy\_05"  Set-VBRvCDCloudCDPPolicy -Policy $policy -SourceProxy $proxy |

Perform the following steps:

1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable.
2. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
3. Run the Set-VBRvCDCloudCDPPolicy cmdlet. Set the $policy variable as the Policy parameter value. Set the $proxy variable as the SourceProxy parameter value.

Related Commands

* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)
* [Get-VBRCDPProxy](get-vbrcdpproxy.md)


