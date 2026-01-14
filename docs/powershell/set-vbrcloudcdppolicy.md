---
title: "Set-VBRCloudCDPPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudcdppolicy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudCDPPolicy

In this article

Short Description

Modifies a cloud CDP policy.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudCDPPolicy -Policy <VBRCloudCDPPolicy> [-Entity <IViItem[]>] [-Server <VBRCloudServer>] [-Datastore <VBRCloudDatastore>] [-Name <String>] [-Description <String>] [-Suffix <String>] [-SourceProxy <VBRCDPProxy[]>] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-EnableApplicationProcessingOptions] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRCloudServerNetworkInfo[]>] [-EnableReplicaSeeding] [-RepositorySeed <CBackupRepository>] [-EnableReplicaMapping] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <VBRViCloudVM[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a cloud CDP policy.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies a cloud CDP policy that you want to modify. | Accepts the VBRCloudCDPPolicy object. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByValue, |
| Entity | Specifies the array of VMs you want to add to the policy. | Accepts the IViItem[] object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Server | Specifies a cloud host allocated by a service provider through the hardware plan. The cloud CDP replicas will be created in this host. | Accepts the VBRCloudServer object. To get this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | True | Named | False |
| Datastore | Returns datastores or disk volumes allocated under cloud resources. The cmdlet will keep cloud CDP replicas in this datastore. | Accepts the VBRCloudDatastore object. To get this object, run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. | True | Named | False |
| Name | Specifies the name you want to assign to a policy. | String | False | Named | False |
| Description | Specifies a description of a policy. | String | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Note: If you omit this parameter, the replicated VMs will get the '\_replica' suffix. | String | False | Named | False |
| SourceProxy | Specifies an array of CDP source proxies added to the backup infrastructure. The cmdlet will use these proxies to transfer data.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings of a cloud CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet | False | Named | False |
| RetentionOptions | Specifies retention settings of a cloud CDP policy. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |
| EnableApplicationProcessingOptions | Enables guest processing settings for a cloud CDP policy.  Use the GuestProcessingOptions parameter to specify the guest processing settings. | SwitchParameter | False | Named | False |
| GuestProcessingOptions | Specifies guest processing settings of a cloud CDP policy. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| EnableNetworkMapping | Enables network mapping.  To set the network mapping rules, use the following parameters:   * SourceNetwork * TargetNetwork | SwitchParameter | False | Named | False |
| SourceNetwork | For network mapping.  Specifies an array of production networks to which the VMs added to a cloud CDP policy are connected.  Note: The number of source networks must match the number of target networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For network mapping.  Specifies an array of networks in the disaster recovery site. VMs that are replicated with the cloud CDP policy will be connected to these networks.  Note: The number of source networks must match the number of target networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| EnableReplicaSeeding | Enables replica seeding.  To specify replica seeding repository settings, use the RepositorySeed parameter. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies a backup repository that keeps a full backup of VMs that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReplicaMapping | Enables replica mapping. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies an array of production VMs that you want to replicate using replica mapping.  The cloud CDP policy will map this VM to the VM in the disaster recovery site.  Use the ReplicaVM parameter to specify the replicated VM on the disaster recovery site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies an array VM in the disaster recovery site. The cmdlet will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a cloud CDP policy without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCloudCDPPolicy object that contains cloud CDP policy settings.

Examples

Modifying Source Proxies for Cloud CDP Policy

This example shows how to change the CDP source proxies for the DB\_replication cloud CDP policy. The cmdlet will set the Proxy\_05 to transfer the replica data.

|  |
| --- |
| $policy = Get-VBRCDPPolicy -Name "DB\_replication"  $proxy = Get-VBRCDPProxy -Name "Proxy\_05"  Set-VBRCloudCDPPolicy -Policy $policy -SourceProxy $proxy |

Perform the following steps:

1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable.
2. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
3. Run the Set-VBRCloudCDPPolicy cmdlet. Set the $policy variable as the Policy parameter value. Set the $proxy variable as the SourceProxy parameter value.

Related Commands

* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)
* [Get-VBRCDPProxy](get-vbrcdpproxy.md)

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
