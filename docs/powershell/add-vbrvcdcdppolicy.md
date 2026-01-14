---
title: "Add-VBRvCDCDPPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcdcdppolicy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Add-VBRvCDCDPPolicy

In this article

Short Description

Creates a Cloud Director CDP policy.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCDCDPPolicy -SourceObject <IVcdItem[]> -OrganizationVdc <CVcdOrganizationVdcItem> -GeneralStoragePolicy <CVcdOrgVdcStorageProfile> [-Name <string>] [-Description <string>] [-ExcludedObject <IVcdItem[]>] [-SourceNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-TargetNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-RepositorySeed <CBackupRepository>] [-OriginalVApp <CVcdVappItem[]>] [-ReplicaVApp <CVcdVappItem[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy <VBRCDPProxy[]>] [-Suffix <string>] [-CompressionLevel {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a Cloud Director CDP policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceObject | Specifies an array of vApps that you want to replicate. | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| OrganizationVdc | Specifies the organization VDC where replicas will be stored. | Accepts the CVcdOrganizationVdcItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| GeneralStoragePolicy | Specifies the storage policy according to which the cmdlet will create replicas. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| Name | Specifies a name for the CDP policy. | String | False | Named | False |
| Description | Specifies a description for the CDP policy. | String | False | Named | False |
| ExcludedObject | Specifies an array of VM containers that you want to exclude from the CDP policy. You can exclude the following types of containers:   * Organization * Organization VDC * vApp | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| SourceNetwork | For the network mapping functionality.  Specifies an array of the production networks to which the vApps are connected.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For the network mapping functionality.  Specifies an array of the networks in the Disaster Recovery site. The replicated vApps will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| RepositorySeed | For the replica seeding functionality.  Specifies the backup repository that keeps the full backups of vApps that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVApp | For the replica mapping functionality.  Specifies an array of production vApps for which you plan to use replica mapping.  The CDP policy will map these vApps to the vApps in the disaster recovery site.  Use the ReplicaVApp parameter to specify the vApps in the disaster recovery site. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| ReplicaVApp | For the replica mapping functionality.  Specifies an array of vApps in the disaster recovery site. The cmdlet will map the production vApps to these vApps and will use these vApps as replicas.  Use the OriginalVApp parameter to specify the vApps in the production site. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies an array of the CDP proxy in the production site that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies an array of the target CDP proxies that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of vApps replicated with CDP policies.  Default: "\_replica". | String | False | Named | False |
| CompressionLevel | Specifies the compression level for the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | VBRCompressionLevel | False | Named | False |
| NotificationOptions | Specifies notification options of the CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |
| GuestProcessingOptions | Specifies guest processing options. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDCDPPolicy object that defines settings of the CDP policy.

Examples

Creating Cloud Director CDP Policy

This example shows how to create a Cloud Director CDP policy.

|  |
| --- |
| $server = Get-VBRServer -Name "Cloud Server"  $vapp = Find-VBRvCloudEntity -Server $server -VApp  $organization = Find-VBRvCloudEntity -Server $server -OrganizationVdc  $policy = Find-VBRvCloudEntity -Server $server -StorageProfile -Name "Default Storage policy" | Where OrgVcdRef -eq $organization.VcdRef  Add-VBRvCDCDPPolicy -SourceObject $vapp -OrganizationVdc $organization -GeneralStoragePolicy $policy |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Server and VApp parameters values. Save the result to the $vapp variable.
3. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Server and OrganizationVdc parameters values. Save the result to the $organization variable.
4. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Server, StorageProfile and Name parameters values. Save the result to the $policy variable.
5. Run the Add-VBRvCDCDPPolicy cmdlet. Set the $vapp variable as the SourceObject parameter value. Set the $organization variable as the OrganizationVdc parameter value. Set the $policy variable as the GeneralStoragePolicy parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
