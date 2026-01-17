---
title: "Get-VEPSQLInstance"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlinstance.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---

# Get-VEPSQLInstance


Short Description

Returns backed-up PostgreSQL instances.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLInstance [-Session] <VEPSQLRestoreSession> [-DataDirectory <string>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up PostgreSQL instances.

After you get backed-up PostgreSQL instances, you can perform the following operations with these instances:

* Run the [Start-VEPSQLInstanceRestore](start-vepsqlinstancerestore.md) cmdlet to restore PostgreSQL instances.
* Run the [Start-VEPSQLInstancePublish](start-vepsqlinstancepublish.md) cmdlet to publish PostgreSQL instances.
* Run the [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md) cmdlet to instantly recover PostgreSQL instances.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return an array of PostgreSQL instances within the specified restore session. | Accepts the [VEPSQLRestoreSession](vepsqlrestoresession.md) object. To get this object, run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| DataDirectory | Specifies a path to the data directory of the backed-up PostgreSQL instance. The cmdlet will return the PostgreSQL instance with the specified data directory. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstance](vepsqlinstance.md)[] array that contains backed-up PostgreSQL instances.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting PostgreSQL Instances Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get all PostgreSQL instances included in a PostgreSQL restore session.  |  | | --- | | $session = Get-VEPSQLRestoreSession  Get-VEPSQLInstance -Session $session[0] |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEPSQLInstance cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting PostgreSQL Instance with Specified Data Directory

|  |  |
| --- | --- |
| This example shows how to get a specific PostgreSQL instance included in a PostgreSQL restore session.  |  | | --- | | $session = Get-VEPSQLRestoreSession  Get-VEPSQLInstance -Session $session[0] -DataDirectory /var/lib/pgsql/13/data |  Perform the following steps:   1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEPSQLInstance cmdlet. Set the $session variable as the Session parameter value. Specify the DataDirectory parameter value. |

Related Commands

[Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)


