---
title: "New-VBRUniversalCDPViDestination"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbruniversalcdpvidestination.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# New-VBRUniversalCDPViDestination

In this article

Short Description

Defines the target location settings for universal CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Target universal CDP policies to a VMware vSphere cluster.

|  |
| --- |
| New-VBRUniversalCDPViDestination -TargetCluster <CViClusterItem> [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-DiskType {Source | Thick | Thin | ThickEagerZeroed | Mixed}] [<CommonParameters>] |

* Target universal CDP policies to an ESXi host.

|  |
| --- |
| New-VBRUniversalCDPViDestination -TargetHost <CEsxItem> [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-DiskType {Source | Thick | Thin | ThickEagerZeroed | Mixed}] [<CommonParameters>] |

Detailed Description

This cmdlet defines the IUniversalCdpDestination object. This object contains the target location settings for universal CDP policies.

The target ESXi host or cluster must have the I/O CDP filter installed. For more information on how to install the filter, see [Install-VBRCDPFilter](install-vbrcdpfilter.md).

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TargetCluster | Specifies a target cluster. The cmdlet will replicate workloads to this cluster. | Accepts the CViClusterItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| TargetHost | Specifies a target ESXi host. The cmdlet will replicate workloads to this ESXi host. | Accepts the CEsxItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| ResourcePool | Specifies the resource pool to which you want to replicate workloads. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder to which you want to replicate workloads. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Datastore | Specifies the datastore to which you want to replicate workloads. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy that must be applied to the replica virtual disks. | Accepts the VBRViStoragePolicy object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| DiskType | Specifies the type of disks for replicas:   * Source: the restored replica disks will be the same format as source. * Thick: the restored replica disks will be thick. * Thin: the restored replica disks will be thin.  * ThickEagerZeroed: the restored replica disks will be thick eager zeroed. | VBRDiskCreationMode | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUniversalCDPViDestination object that defines the target location settings for universal CDP policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Target Location Settings for Universal CDP Policy (Cluster)

|  |  |
| --- | --- |
| This example shows how to create target location settings for the universal CDP policy. The target location is a cluster.  |  | | --- | | $cluster = Find-VBRViEntity -Name "CDP cluster"  $pool = Find-VBRViEntity -ResourcePools -Name Rep-Org-Ti\*  $destination = New-VBRUniversalCDPViDestination -TargetCluster $cluster -ResourcePool $pool |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $cluster variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the ResourcePools and Name parameter values. Save the result to the $pool variable. 3. Run the New-VBRUniversalCDPViDestination cmdlet. Set the $cluster variable as the TargetCluster parameter value. Set the $pool variable as the ResourcePool parameter value. Save the result to the $destination variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Target Location Settings for Universal CDP Policy (Host)

|  |  |
| --- | --- |
| This example shows how to create target location settings for the universal CDP policy. The target location is an ESXi host.  |  | | --- | | $host = Find-VBRViEntity -Name "prgtwesx01-virt.tech.local"  $destination = New-VBRUniversalCDPViDestination -TargetHost $host -DiskType "Thin" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 2. Run the New-VBRUniversalCDPViDestination cmdlet. Set the $server variable as the TargetHost parameter value. Specify the DiskType parameter value. Save the result to the $destination variable. |

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
