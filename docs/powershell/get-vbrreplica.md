---
title: "Get-VBRReplica"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrreplica.html"
last_updated: "7/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRReplica

In this article

Short Description

Returns replica objects of VMs or cloud VMs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRReplica [-Name <string[]>] [-Type <VBRReplicaType> {Local | Cloud | Tenant}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns replica objects of VMs or cloud VMs created by Veeam Backup & Replication.

You can look for all replica objects or for replica objects created by a particular replication job.

With this cmdlet, you can get the replica objects that are managed by your backup console. In case you have removed some replica objects from the Veeam Backup & Replication console, but they remain on disk, you will not be able to get them.

|  |
| --- |
| Tip |
| Consider the following:   * To get restore points of replicas, use the [Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md) cmdlet. * To get information about replicas, use the [Get-VBRBackupObject](get-vbrbackupobject.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of the replication job names. The cmdlet will return replica objects produced by these jobs. | String[] | False | Named | False |
| Type | Specifies the type of the replica objects you want to get:   * Local: non-cloud replica objects. * Cloud: [for cloud user] cloud replica objects. * Tenant: [for cloud provider] cloud replica objects created by cloud user. | VBRReplicaType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackup object that contains replica objects created by Veeam Backup & Replication.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Replicas

|  |  |
| --- | --- |
| This command looks for all replica objects created by Veeam Backup & Replication.  |  | | --- | | Get-VBRReplica | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Replica by Job Name

|  |  |
| --- | --- |
| This command looks for the replica objects created by the replication job.  |  | | --- | | Get-VBRReplica -Name "DC Replica" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Local Replica by Job Name

|  |  |
| --- | --- |
| This command looks for the local (non-cloud) replica objects created with the replication job.  |  | | --- | | Get-VBRReplica -Type Local -Name "DC Replica" | |

Page updated 7/17/2024

Page content applies to build 13.0.1.1071
