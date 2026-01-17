---
title: "Get-VEHANADatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanadatabase.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backed-up SAP HANA databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEHANADatabase [-System] <VEHANASystem> [-Name <String>] [-Tenant] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up databases located on the specified SAP HANA system. After you get the backed-up SAP HANA databases, you can use the [Start-VEHANADatabaseRestore](start-vehanadatabaserestore.md) cmdlet to restore the SAP HANA databases you need.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| System | Specifies the name of the SAP HANA system on which the databases reside. The cmdlet will return the databases on the specified SAP HANA system. | Accepts the [VEHANASystem](vehanasystem.md) object. To get this object, run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies the name of an SAP HANA database. The cmdlet will return the SAP HANA database with the specified name. | String | False | Named | False |
| Tenant | Defines that the cmdlet returns only the tenant databases on the selected SAP HANA system. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANADatabase](vehanadatabase.md)[] array that contains backed-up SAP HANA databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Databases on the Specified System

|  |  |
| --- | --- |
| This example shows how to return all SAP HANA databases on a backed-up SAP HANA system.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = Get-VEHANADatabase -System $system |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $system variable. 2. Run the Get-VEHANADatabase cmdlet. Set the $system variable as the System parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Tenant Databases on the Specified System

|  |  |
| --- | --- |
| This example shows how to return only the tenant databases that reside on the selected SAP HANA system.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = Get-VEHANADatabase -System $system -Tenant |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $system variable.  1. Run the Get-VEHANADatabase cmdlet. Set the $system variable as the System parameter value. Provide the Tenant parameter to only return the tenant databases on the selected system. Save the result to the $database variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting SAP HANA Database with Specified Name

|  |  |
| --- | --- |
| This example shows how to get a specific SAP HANA database using its name.  |  | | --- | | $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem -Session $session[0]  $database = Get-VEHANADatabase -System $system -Name "Tenant1" |  Perform the following steps:   1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $system variable.  1. Run the Get-VEHANADatabase cmdlet. Set the $system variable as the System parameter value. Specify the name of the necessary database as the Name parameter value. Save the result to the $database variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VEHANARestoreSession](get-vehanarestoresession.md)
* [Get-VEHANASystem](get-vehanasystem.md)

Page updated 7/29/2025

Page content applies to build 13.0.1.1071
