---
title: "Restart-VEHANADatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restart-vehanadatabaserestore.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restarts a failed restore job for an SAP HANA database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restart-VEHANADatabaseRestore -RestoreJob <VEHANARestore> [<CommonParameters>] |

Detailed Description

This cmdlet restarts a failed restore job for an SAP HANA database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestoreJob | Specifies the SAP HANA restore job that you want to restart. | Accepts the [VEHANARestore](vehanarestore.md) object. To get this object, run the [Get-VEHANADatabaseRestore](get-vehanadatabaserestore.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Restarting SAP HANA Restore Process

This example shows how to restart a failed restore job for an SAP HANA database.

|  |
| --- |
| $restorejob = Get-VEHANADatabaseRestore  Restart-VEHANADatabaseRestore -RestoreJob $restorejob[0] |

Perform the following steps:

1. Run the [Get-VEHANADatabaseRestore](get-vehanadatabaserestore.md) cmdlet. Save the result to the restorejob variable.

The cmdlet will return an array of restore jobs. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.

1. Run the Restart-VEHANADatabaseRestore cmdlet. Set the $restorejob variable as the RestoreJob parameter value.

Related Commands

[Get-VEHANADatabaseRestore](get-vehanadatabaserestore.md)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
