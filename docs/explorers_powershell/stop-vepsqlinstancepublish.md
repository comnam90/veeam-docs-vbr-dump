---
title: "Stop-VEPSQLInstancePublish"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vepsqlinstancepublish.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Stop-VEPSQLInstancePublish


Short Description

Unpublishes a PostgreSQL instance from the target server.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEPSQLInstancePublish [-InstancePublish] <VEPSQLInstancePublish> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet unpublishes a PostgreSQL instance from the target server.

|  |
| --- |
| Note |
| Publishing sessions will not stop automatically if you close the PowerShell console. To stop a publishing session, you must run the Stop-VEPSQLInstancePublish cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstancePublish | Specifies the publishing process for a PostgreSQL instance. The cmdlet will stop the process and unpublish the instance from the target PostgreSQL server. | Accepts the [VEPSQLInstancePublish](vepsqlinstancepublish.md) object. To get this object, run the [Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md) cmdlet. | True | 0 | True |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Publishing Process for a PostgreSQL Instance

This example shows how to unpublish a PostgreSQL instance.

|  |
| --- |
| $publish = Get-VEPSQLInstancePublish -InstanceName "rhel01:5433"  Stop-VEPSQLInstancePublish -InstancePublish $publish |

Perform the following steps:

1. Run the [Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md) cmdlet. Specify the InstanceName parameter value and save the result to the $publish variable.
2. Run the Stop-VEPSQLInstancePublish cmdlet. Set the $publish variable as the InstancePublish parameter value.

Related Commands

[Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md)


