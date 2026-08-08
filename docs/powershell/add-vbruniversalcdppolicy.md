---
title: "Add-VBRUniversalCDPPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbruniversalcdppolicy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Add-VBRUniversalCDPPolicy


Short Description

Creates a universal CDP policy.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRUniversalCDPPolicy -SourceObject <VBRUniversalCDPSource[]> [-ExcludedObject <VBRUniversalCDPSource[]>] -Destination <IUniversalCdpDestination> [-Name <string>] [-Description <string>] [-NetworkMapping <VBRUniversalCDPNetworkMappingRule[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy <VBRCDPProxy[]>] [-Suffix <string>] [-CompressionLevel {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-RepositorySeed <CBackupRepository>] [-OriginalMachine <VBRDiscoveredComputer[]>] [-ReplicaMachine <VBRNamedObject[]>] [-GuestProcessingOptions <VBRApplicationProcessingOptions[]>] [-ReIpRule <IViReIpRule[]>] [<CommonParameters>] |

Detailed Description

This cmdlet creates a universal CDP policy.

|  |
| --- |
| Note |
| The cmdlet creates a CDP policy in the disabled state unless you enable a policy schedule. Run the [Enable-VBRCDPPolicy](enable-vbrcdppolicy.md) cmdlet to enable the policy. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| SourceObject | Specifies the workloads or protection groups that you want to protect with universal CDP. | Accepts the VBRUniversalCDPSource[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) or [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ExcludedObject | Specifies the array of workloads that you want to exclude from the universal CDP policy processing. | Accepts the VBRUniversalCDPSource[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | False |
| Destination | Specifies the settings of the target location where the workloads will be replicated. | Accepts the IUniversalCdpDestination object. To create this object, run the [New-VBRUniversalCDPViDestination](new-vbruniversalcdpvidestination.md) or [New-VBRUniversalCDPCloudDestination](new-vbruniversalcdpclouddestination.md) cmdlet. | True | Named | False |
| Name | Specifies a name for the universal CDP policy. | String | False | Named | False |
| Description | Specifies a description for the universal CDP policy. | String | False | Named | False |
| NetworkMapping | Specifies the array of network mapping settings. | Accepts the VBRUniversalCDPNetworkMappingRule[] object. To get this object, run the [New-VBRUniversalCDPNetworkMappingRule](new-vbruniversalcdpnetworkmappingrule.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the array of the source CDP proxies that you want to use.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the array of the target CDP proxies that you want to use.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of replicas.  Default: "\_replica". | String | False | Named | False |
| CompressionLevel | Specifies the compression level of the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | [VBRCompressionLevel](enums.md#VBRCompressionLevel) | False | Named | False |
| NotificationOptions | Specifies notification settings of the universal CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings of the universal CDP policy. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |
| RepositorySeed | For replica seeding. Specifies the backup repository that keeps a full backup of workloads that you want to replicate.  Note: Backups for seeding must be created by Veeam Agent for Linux or Veeam Agent for Microsoft Windows. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalMachine | For replica mapping.  Specifies an array of production workloads that you want to replicate using replica mapping.  The universal CDP policy will map these workloads to the workloads in the disaster recovery site.  Use the ReplicaMachine parameter to specify the replicated workloads on the disaster recovery site. | Accepts the VBRDiscoveredComputer[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | False |
| ReplicaMachine | For replica mapping.  Specifies an array of workloads on the disaster recovery site.  The cmdlet will map the production workloads to these workloads.  Use the OriginalMachine parameter to specify the production workloads. | Accepts the VBRNamedObject[] object. To get this object, run the [Get-VBRViVM](get-vbrvivm.md) , [Get-VBRViCloudVM](get-vbrvicloudvm.md) or [Get-VBRvCDCloudVM](get-vbrvcdcloudvm.md) cmdlet. | False | Named | False |
| GuestProcessingOptions | Specifies the array of guest processing settings for the universal CDP policy. | Accepts the VBRApplicationProcessingOptions[] object. To create this object, run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| ReIpRule | Specifies the array of re-IP rules. Use re-IP rules when the workloads must be replicated to a network with a different IP addressing scheme. | Accepts the IViReIpRule[] object. To get this object, run the [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUniversalCDPPolicy object that defines settings of the universal CDP policy.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Universal CDP Policy

|  |  |
| --- | --- |
| This example shows how to create the Universal CDP policy that will replicate the CDP Protection Group to the cluster.  |  | | --- | | $cluster = Find-VBRViEntity -Name "CDP cluster"  $server = Get-VBRServer -Name "prgtwesx01-virt.tech.local"  $pool = Find-VBRViEntity -Server $server -ResourcePools -Name Rep-Org-Ti\*  $destination = New-VBRUniversalCDPViDestination -TargetCluster $cluster -ResourcePool $pool  $group = Get-VBRProtectionGroup -Name "Protection Group CDP"  $policy = Add-VBRUniversalCDPPolicy -SourceObject $group -Destination $destination -Name "Universal CDP Policy PS" -Description "Universal CDP for protection group" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $cluster variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the ResourcePools and Name parameter values. Save the result to the $pool variable. 4. Run the [New-VBRUniversalCDPViDestination](new-vbruniversalcdpvidestination.md) cmdlet. Set the $cluster variable as the TargetCluster parameter value. Set the $pool variable as the ResourcePool parameter value. Save the result to the $destination variable. 5. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 6. Run the Add-VBRUniversalCDPPolicy cmdlet. Specify the following settings:  * Set the $group variable as the SourceObject parameter value. * Set the $destination variable as the Destination parameter value. * Specify the Name parameter value. * Specify the Description parameter value. * Save the result to the $policy variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Universal CDP Policy with Guest Processing

|  |  |
| --- | --- |
| This example shows how to create a universal CDP policy with application-aware processing enabled for Windows workloads.  |  | | --- | | $cluster = Find-VBRViEntity -Name "CDP cluster"  $server = Get-VBRServer -Name "prgtwesx01-virt.tech.local"  $pool = Find-VBRViEntity -Server $server -ResourcePools -Name Rep-Org-Ti\*  $destination = New-VBRUniversalCDPViDestination -TargetCluster $cluster -ResourcePool $pool  $group = Get-VBRProtectionGroup -Name "Protection Group CDP"  $guestprocessing = New-VBRApplicationProcessingOptions -BackupObject $group -OSPlatform Windows -Enable -GeneralTransactionLogAction ProcessLogsWithJob  Add-VBRUniversalCDPPolicy -SourceObject $group -Destination $destination -Name "Universal CDP Policy PS" -Description "Universal CDP for protection group" -GuestProcessingOptions $guestprocessing |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $cluster variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the ResourcePools and Name parameter values. Save the result to the $pool variable. 4. Run the [New-VBRUniversalCDPViDestination](new-vbruniversalcdpvidestination.md) cmdlet. Set the $cluster variable as the TargetCluster parameter value. Set the $pool variable as the ResourcePool parameter value. Save the result to the $destination variable. 5. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 6. Run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. Specify the following settings:  * Set the $group variable as the BackupObject parameter value. * Set the Windows value as the OSPlatform parameter value. * Provide the Enable parameter. * Set the ProcessLogsWithJob value as the GeneralTransactionLogAction parameter value. * Save the result to the $guestprocessing variable.  1. Run the Add-VBRUniversalCDPPolicy cmdlet. Specify the following settings:  * Set the $group variable as the SourceObject parameter value. * Set the $destination variable as the Destination parameter value. * Specify the Name parameter value. * Specify the Description parameter value. * Set the $guestprocessing variable as the GuestProcessingOptions parameter value. |

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCDPProxy](get-vbrcdpproxy.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md)
* [Get-VBRViVM](get-vbrvivm.md)
* [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md)
* [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRUniversalCDPNetworkMappingRule](new-vbruniversalcdpnetworkmappingrule.md)
* [New-VBRUniversalCDPViDestination](new-vbruniversalcdpvidestination.md)

Page updated 2026-05-27

