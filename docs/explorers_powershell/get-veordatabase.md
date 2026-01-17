---
title: "Get-VEORDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veordatabase.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backed-up Oracle databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORDatabase [-Session] <VEORRestoreSession> [[-Name] <String[]>] [-OracleHome <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Oracle databases. After you get backed-up Oracle databases, you can restore these databases.

Run the [Restore-VEORDatabase](restore-veordatabase.md) cmdlet to restore Oracle databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session. The cmdlet will return an array of Oracle databases within the specified restore session. | Accepts the [VEORRestoreSession](veorrestoresession.md) object. To get this object, run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of names for Oracle databases. The cmdlet will return information about databases with the specified names. | String[] | False | 1 | False |
| OracleHome | Specifies an array of names of an Oracle home path. The cmdlet will return the Oracle home paths with the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORDatabase](veordatabase.md)[] array that contains backed-up Oracle databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Oracle Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get a list of all Oracle databases within the specified restore session.  |  | | --- | | $session = Get-VEORRestoreSession  Get-VEORDatabase -Session $session[0] |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEORDatabase cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Oracle Databases with Specified Name

|  |  |
| --- | --- |
| This example shows how to get all Oracle databases with a specific name within the specified restore session.  |  | | --- | | $session = Get-VEORRestoreSession  Get-VEORDatabase -Session $session[0] -Name "orcl" |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEORDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Oracle Databases with Specific Names Located in Specific Oracle Home Directories

|  |  |
| --- | --- |
| This example shows how to get Oracle databases with the specified names that are located in the specified Oracle Home directories.  |  | | --- | | $session = Get-VEORRestoreSession  $dbnames = @("orcl1", "orcl2")  $oraclehomepaths = @("E:\app\administrator\product\19.3.0\dbhome\_1", "E:\app\administrator\product\19.3.0\dbhome\_2")  Get-VEORDatabase -Session $session[0] -Name @dbnames -OracleHome @oraclehomepaths |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary Oracle databases. 2. Declare the $oraclehomepaths variable. Assign to this variable an array with the necessary Oracle Home paths. 3. Run the Get-VEORDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Set the @dbnames variable as the Name parameter value. Set the @oraclehomepaths variable as the OracleHome parameter value. |

Related Commands

[Get-VEORRestoreSession](get-veorrestoresession.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
