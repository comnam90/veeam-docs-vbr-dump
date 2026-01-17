---
title: "Get-VEORPublishedDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorpublisheddatabase.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns published Oracle databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORPublishedDatabase [-Session] <VEORRestoreSession> [[-Name] <String[]>] [-Sever <String[]>] [-Server <String[]>] [-OracleHome <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns published Oracle databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will return information about a published Oracle database added to the specified restore session. | Accepts the [VEORRestoreSession](veorrestoresession.md) object. To get this object, run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet | True | 0 | True |
| Name | Specifies an array of names for Oracle databases. The cmdlet will return information about published databases with the specified names. | String[] | False | 1 | False |
| Sever | Note: This parameter is deprecated and will become obsolete in a future version. Use the Server parameter instead.  Specifies an array of target Oracle server names (as DNS names or IP addresses). The cmdlet will return information about published databases located on these servers. | String[] | False | Named | False |
| Server | Specifies an array of target Oracle server names (as DNS names or IP addresses). The cmdlet will return information about published databases located on these servers. | String[] | False | Named | False |
| OracleHome | Specifies an array of target Oracle home paths. The cmdlet will return information about published databases with the specified target Oracle home paths. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORPublishedDatabase](veorpublisheddatabase.md)[] array that contains settings of published Oracle databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published Oracle Databases

|  |  |
| --- | --- |
| This example shows how to get an array of all published Oracle databases.  |  | | --- | | $session = Get-VEORRestoreSession  Get-VEORPublishedDatabase -Session $session[0] |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).   1. Run the Get-VEORPublishedDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Published Oracle Databases with Specified Name

|  |  |
| --- | --- |
| This example shows how to get all Oracle databases with a specific name within the specified restore session.  |  | | --- | | $session = Get-VEORRestoreSession  Get-VEORPublishedDatabase -Session $session[0] -Name "orcl" |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEORPublishedDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Oracle Databases with Specific Names Located in Specific Oracle Home Directories

|  |  |
| --- | --- |
| This example shows how to get Oracle databases with the specified names that are located in the specified Oracle Home directories.  |  | | --- | | $session = Get-VEORRestoreSession  $dbnames = @("orcl1", "orcl2")  $oraclehomepaths = @("E:\app\administrator\product\19.3.0\dbhome\_1", "E:\app\administrator\product\19.3.0\dbhome\_2")  Get-VEORPublishedDatabase -Session $session[0] -Name @dbnames -OracleHome @oraclehomepaths |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary Oracle databases. 2. Declare the $oraclehomepaths variable. Assign to this variable an array with the necessary Oracle Home paths. 3. Run the Get-VEORPublishedDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Set the @dbnames variable as the Name parameter value. Set the @oraclehomepaths variable as the OracleHome parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Oracle Databases Published on Specific Servers

|  |  |
| --- | --- |
| This example shows how to get an array of all Oracle databases published on the specified servers.  |  | | --- | | $session = Get-VEORRestoreSession  $servernames = @("winorcl01.tech.local", "winorcl02.tech.local")  Get-VEORPublishedDatabase -Session $session -Server $servernames |  Perform the following steps:   1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $servernames variable. Assign to this variable an array with the names of the necessary servers with Oracle. 2. Run the Get-VEORPublishedDatabase cmdlet. Set the $session variable as the Session parameter value. Set the $servernames variable as the Server parameter value. |

Related Commands

[Get-VEORRestoreSession](get-veorrestoresession.md)

Page updated 3/5/2025

Page content applies to build 13.0.1.1071
