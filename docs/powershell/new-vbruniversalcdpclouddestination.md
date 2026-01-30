---
title: "New-VBRUniversalCDPCloudDestination"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbruniversalcdpclouddestination.html"
last_updated: "10/13/2025"
product_version: "13.0.1.1071"
---

# New-VBRUniversalCDPCloudDestination


Short Description

Defines the target location settings for cloud universal CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRUniversalCDPCloudDestination -Datastore <VBRCloudDatastore> [-DiskType {Source | Thick | Thin | ThickEagerZeroed | Mixed}] [-Force] [-HighPriority] -Server <VBRCloudServer>  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRUniversalCDPCloudDestination object that contains the target location settings for cloud universal CDP policies.

The target ESXi host or cluster must have the I/O CDP filter installed. For more information oh how to install the filter, see [Install-VBRCDPFilter](install-vbrcdpfilter.md).

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Datastore | Specifies the datastore under your cloud resources. The cmdlet will replicate workloads to this datastore. | Accepts the [VBRCloudDatastore](vbrclouddatastore.md) object. To get this object, run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. | True | Named | False |
| Server | Specifies the cloud host allocated by the service provider. The cmdlet will replicate workloads to this cloud host. | Accepts the [VBRCloudServer](vbrcloudserver.md) object. To get this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | True | Named | False |
| DiskType | Specifies the type of disks for replicas:   * Source: the replica disks will be the same format as source. * Thick: the replica disks will be thick. * Thin: the replica disks will be thin.  * ThickEagerZeroed: the replica disks will be thick eager zeroed. | VBRDiskCreationMode | False | Named | False |
| Force | Defines that the cmdlet will perform a failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUniversalCDPCloudDestination object that defines the target location settings for cloud universal CDP policies.

Examples

Creating Target Location Settings for Cloud Universal CDP Policy

This example shows how to create target location settings for the cloud universal CDP policy. The replica disks will be the same format as source disks.

|  |
| --- |
| $datastore = Get-VBRCloudDatastore -Name "Cloud Replicas"  $server = Get-VBRCloudServer -Name "Atlanta Silver"  $destination = New-VBRUniversalCDPCloudDestination -Datastore $datastore -DiskType Source -Server $server |

Perform the following steps:

1. Run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. Specify the Name parameter value. Save the result to the $datastore variable.
2. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
3. Run the New-VBRUniversalCDPCloudDestination cmdlet. Specify the following settings:

* Set the $datastore variable as the Datastore parameter value.
* Set the Source value as the DiskType parameter value.
* Set the $server variable as the Server parameter value.
* Save the result to the $destination variable.

Related Commands

* [Get-VBRCloudDatastore](get-vbrclouddatastore.md)
* [Get-VBRCloudServer](get-vbrcloudserver.md)


