---
title: "Set-VBRCDPPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcdppolicy.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCDPPolicy

In this article

Short Description

Modifies CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCDPPolicy -Policy <VBRCDPPolicy> [-Entity <IViItem[]>] [-Exclusions <IViItem[]>] [-Name <String>] [-Description <String>] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-ReIpRule <IViReIpRule[]>] [-SourceProxy <VBRCDPProxy[]>] [-TargetProxy <VBRCDPProxy[]>] [-Suffix <String>] [-CompressionLevel <VBRCompressionLevel>] [-NotificationOptions <VBRNotificationOptions>] [-RetentionOptions <VBRCDPPolicyRetentionOptions>] [-EnableReplicaSeeding] [-RepositorySeed <CBackupRepository>] [-EnableReplicaMapping] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <CViVmItem[]>] [-EnableApplicationProcessingOptions] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies CDP policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies a CDP policy that you want to modify. | Accepts the VBRCDPPolicyBase[] object. To get this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Entity | Specifies an array of VMs that you want to add to a CDP policy. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Exclusions | Specifies an array of VMs that you want to exclude from the CDP policy processing. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Name | Specifies a name for the CDP policy. The cmdlet will replace a CDP policy name with this name. | String | False | Named | False |
| Description | Specifies a description for the CDP policy. The cmdlet will replace a CDP policy description with this description. | String | False | Named | False |
| ResourcePool | Specifies a resource pool to which you want to replicate. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Folder | Specifies a folder to which you want to replicate VMs. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Datastore | Specifies a datastore to which you want to replicate VMs. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies a VMware storage policy that must be applied to the replica virtual disks. | Accepts the VBRViStoragePolicy object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| EnableNetworkMapping | Enables network mapping. | SwitchParameter | False | Named | False |
| SourceNetwork | For network mapping.  Specifies an array of production networks to which the VMs in the CDP policy are connected.  Note: The number of the source and the target networks must be the same. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For network mapping.  Specifies an array of networks in the disaster recovery site. The replicated VMs will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| ReIpRule | Specifies re-IP rules. | Accepts the VBRViReplicaReIpRule or VBRViReplicaReIpIPv6Rule object. To get this object, run the [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the target proxy that you want to assign to the CDP policy.  Default: Automatic selection. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Suffix | Specifies a suffix that the cmdlet will add to the name of the VM the you want to replicate. This name will be used to register the replicated VM on the target server.  Default: "\_replica". | String | False | Named | False |
| CompressionLevel | Note: The parameter is not supported and will be deprecated.  Specifies the compression level of the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | VBRCompressionLevel | False | Named | False |
| NotificationOptions | Specifies notification options of a CDP policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| RetentionOptions | Specifies retention settings of a CDP policy. | Accepts the VBRCDPPolicyRetentionOptions object. To create this object, run the [New-VBRCDPPolicyRetentionOptions](new-vbrcdppolicyretentionoptions.md) cmdlet. | False | Named | False |
| EnableRepositorySeed | Enables the replica seeding option. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies a backup repository that keeps a full backup of a VM that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReplicaMapping | Enables the replica mapping option. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies a production VM that you want to replicate using replica mapping.  The CDP policy will map this VM to the VM on the disaster recovery site.  Use the ReplicaVM parameter to specify the replica VM on the disaster recovery site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies a VM on the disaster recovery site. The cmdlet will map the production VM to this VM, and the CDP policy will replicate data to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| EnableApplicationProcessingOptions | Enables application processing option. | SwitchParameter | False | Named | False |
| GuestProcessingOptions | Specifies guest processing options of a CDP policy. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPPolicy object that defines settings of CDP policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying CDP Policy Excluded VMs

|  |  |
| --- | --- |
| This example shows how to exclude the DB01, DB02, DB03 VMs from the VM079 CDP policy processing.  |  | | --- | | $cdppolicy = Get-VBRCDPPolicy -Name "VM079"  $exludedvm = Find-VBRViEntity -Name "DB01, DB02, DB03"  Set-VBRCDPPolicy -Policy $cdppolicy -Exclusions $exludedvm |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $cdppolicy variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $exludedvm variable. 3. Run the Set-VBRCDPPolicy cmdlet. Set the $cdppolicy variable as the Policy parameter value. Set the $exludedvm variable as the Exclusions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying CDP Policy Source and Target Proxies

|  |  |
| --- | --- |
| This example shows how to assign the WinSrv09 machine as the target proxy and the WinSrv04 machine as the source proxy  to the VM079 CDP policy.  |  | | --- | | $cdppolicy = Get-VBRCDPPolicy -Name "VM079"  $targetproxy = Get-VBRCDPProxy -Name "WinSrv09"  $sourceproxy = Get-VBRCDPProxy -Name "WinSrv04"  Set-VBRCDPPolicy -Policy $cdppolicy -TargetProxy $targetproxy -SourceProxy $sourceproxy |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $cdppolicy variable. 2. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $targetproxy variable. 3. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $sourceproxy variable. 4. Run the Set-VBRCDPPolicy cmdlet. Specify the following settings:  * Set the $cdppolicy variable as the Policy parameter value. * Set the $targetproxy variable as the TargetProxy parameter value. * Set the $sourceproxy variable as the SourceProxy parameter value. |

Related Commands

* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)
* [Get-VBRCDPProxy](get-vbrcdpproxy.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
