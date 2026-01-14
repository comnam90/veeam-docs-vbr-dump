---
title: "Set-VBRvCDCDPPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcdcdppolicy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Set-VBRvCDCDPPolicy

In this article

Short Description

Modifies a Cloud Director CDP policy.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCDCDPPolicy -Policy <VBRvCDCDPPolicy> [-Name <string>] [-Description <string>] [-SourceObject <IVcdItem[]>] [-ExcludedObject <IVcdItem[]>] [-EnableNetworkMapping] [-SourceNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-TargetNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-EnableInitialSeeding] [-RepositorySeed <CBackupRepository>] [-EnableReplicaMapping] [-OriginalVApp <CVcdVappItem[]>] [-ReplicaVApp <CVcdVappItem[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy <VBRCDPProxy[]>] [-Suffix <string>] [-EnableApplicationProcessing] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-CompressionLevel {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a Cloud Director CDP policy.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies the Cloud Director CDP policy that you want to modify. | Accepts the VBRvCDCDPPolicy object. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name for the CDP policy. The cmdlet will replace the CDP policy name with this name. | String | False | Named | False |
| Description | Specifies a description for the CDP policy. The cmdlet will replace the CDP policy description with this description. | String | False | Named | False |
| SourceObject | Specifies an array of the vApps that you want to protect. | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| ExcludedObject | Specifies an array of VM containers that you want to exclude from the CDP policy. You can exclude the following types of Cloud Director source objects:   * Organization * Organization VDC * vApp | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| EnableNetworkMapping | Enables network mapping. | SwitchParameter | False | Named | False |
| SourceNetwork | For the network mapping functionality.  Specifies an array of the production networks to which the vApps are connected.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For the network mapping functionality.  Specifies an array of the networks in the Disaster Recovery site. The replicated vApps will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| EnableInitialSeeding | Enables replica seeding. | SwitchParameter | False | Named | False |
| RepositorySeed | For the replica seeding functionality.  Specifies the backup repository that keeps the full backups of vApps that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReplicaMapping | Enables the replica mapping functionality. | SwitchParameter | False | Named | False |
| OriginalVApp | For the replica mapping functionality.  Specifies an array of productions vApp for which you plan to use replica mapping.  The CDP policy will map these vApps to the vApps in the disaster recovery site.  Use the ReplicaVApp parameter to specify the vApps in the disaster recovery site. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| ReplicaVApp | For the replica mapping functionality.  Specifies an array of vApps in the disaster recovery site. The cmdlet will map the production vApps to these vApps and will use these vApps as replicas.  Use the OriginalVApp parameter to specify the vApps in the production site. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies an array of the CDP proxy in the production site that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies an array of the target CDP proxies that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of vApps replicated with CDP policies. | String | False | Named | False |
| EnableApplicationProcessing | Enables guest processing settings for the CDP policy.  Use the GuestProcessingOptions parameter to specify the guest processing settings. | SwitchParameter | False | Named | False |
| GuestProcessingOptions | Specifies guest processing options. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| CompressionLevel | Specifies the compression level for the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level. | VBRCompressionLevel | False | Named | False |
| NotificationOptions | Specifies notification options of the CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named |  |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDCDPPolicy object that defines settings of the CDP policy.

Examples

Creating Cloud Director CDP Policy

This example shows how to modify the compression level for the replicated data. The cmdlet will set the compression level to dedupe-friendly compression level.

|  |
| --- |
| $policy = Get-VBRCDPPolicy  Set-VBRvCDCDPPolicy -Policy $policy -CompressionLevel DedupeFriendly |

Perform the following steps:

1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the Set-VBRvCDCDPPolicy cmdlet. Set the $policy variable as the Policy parameter value. Specify the CompressionLevel parameter value.

Related Commands

[Get-VBRCDPPolicy](get-vbrcdppolicy.md)

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
