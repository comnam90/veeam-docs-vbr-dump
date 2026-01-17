---
title: "Stop-VEMDBPublishJob"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vemdbpublishjob.html"
last_updated: "9/19/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Unpublishes a MongoDB instance from the target server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEMDBPublishJob -PublishJob <VEMDBInstancePublish> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet unpublishes a MongoDB instance from the target server.

|  |
| --- |
| Note |
| Publishing sessions will not stop automatically if you close the PowerShell console. To stop a publishing session, you must run the Stop-VEMDBPublishJob cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| PublishJob | Specifies the publishing process for a MongoDB instance. The cmdlet will stop the process and unpublish the instance from the target MongoDB server. | Accepts the [VEMDBInstancePublish](vemdbinstancepublish.md) object. To get this object, run the [Get-VEMDBPublishJob](get-vemdbpublishjob.md) cmdlet. | True | Named | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Publishing Process for a MongoDB Instance

This example shows how to unpublish a MongoDB instance.

|  |
| --- |
| $publish = Get-VEMDBPublishjob -SourceInstance "mongodb01:27017"  Stop-VEMDBPublishJob -PublishJob $publish |

Perform the following steps:

1. Run the [Get-VEMDBPublishJob](get-vemdbpublishjob.md) cmdlet. Specify the SourceInstance parameter value. Save the result to the $publish variable.
2. Run the Stop-VEMDBPublishJob cmdlet. Set the $publish variable as the PublishJob parameter value.

Related Commands

[Get-VEMDBPublishJob](get-vemdbpublishjob.md)

Page updated 9/19/2025

Page content applies to build 13.0.1.1071
