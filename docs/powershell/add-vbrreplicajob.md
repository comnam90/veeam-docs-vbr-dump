---
title: "Add-VBRReplicaJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrreplicajob.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Add-VBRReplicaJob (obsolete)

In this article

Short Description

Creates new replication job.

|  |
| --- |
| Note |
| This cmdlet is obsolete and is not supported. Run the [Add-VBRViReplicaJob](add-vbrvireplicajob.md) or [Add-VBRHvReplicaJob](add-vbrhvreplicajob.md) cmdlets to create a new replication job. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Add-VBRReplicaJob [-Name <String>] [-Type <String>] [-Server <CHost>] [-Datastore <Datastore>] -Objects <String[]> [-Suffix <String>] [-Description <String>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to create a new replication job.

Replication is a process of copying a VM from its primary location (source host) to a destination location (redundant target host). Veeam Backup & Replication creates an exact copy of a VM (replica), registers it on the target host and maintains it in synch with the original VM.

Note that when you create a replica job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the string with the name you want to assign to the replication job. | String | True | 1 | False |
| Type | Specifies the string with the type of the created replication job which defines how VM data is retrieved:   * VDDK – Virtual Disk Development Kit (VMware vStorage API) * VCB – VMware Consolidated Backup (legacy mode) * NET – Network replication (legacy mode) | String | False | 2 | False |
| Server | Specifies the host where the created replica should be stored. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 3 | False |
| Datastore | Specifies the datastore where the created replica should reside. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | 4 | False |
| Objects | Specifies the string with the names of VMs that you want to replicate. | String[] | True | Named | True (ByValue, ByProperty Name) |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server. | String | False | Named | False |
| Description | Specifies the description of the replica job. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Replication Job

This example allows you to create a replication job with the following parameters:

* Name of a replication job: Replica1
* Replication type: VDDK
* Variable which contains target host DNS name or IP address: $server
* Variable which contains datastore name: $datastore
* Replicated VM: vm4

|  |
| --- |
| Add-VBRReplicaJob –Name “Replica1” –Type VDDK –Server $server –Datastore $datastore –Objects vm4 |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
