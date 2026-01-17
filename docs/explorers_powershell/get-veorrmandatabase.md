---
title: "Get-VEORRMANDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorrmandatabase.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# Get-VEORRMANDatabase


Short Description

Returns Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORRMANDatabase [-Session] <VEORRMANRestoreSession> [[-Name] <String[]>] [-OracleHome <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active restore session for an Oracle database backed-up with Veeam Plug-in for Oracle RMAN. The cmdlet will return an array of Oracle databases backed-up with Veeam Plug-in for Oracle RMAN within the specified restore session. | Accepts the [VEORRMANRestoreSession](veorrmanrestoresession.md) object. To get this object, run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. | True | 0 | False |
| Name | Specifies an array of Oracle database names. The cmdlet will return Oracle databases with the specified names from the restore session. | String[] | False | 1 | False |
| OracleHome | Specifies an array of Oracle home paths. The cmdlet will return Oracle databases from the restore session with the specified paths. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORRMANDatabase](veorrmandatabase.md)[] array that contains Oracle databases backed up by Veeam Plug-in for Oracle RMAN.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Databases Within Specified Restore Session

|  |  |
| --- | --- |
| This example shows how to get all Oracle databases backed up with Veeam Plug-in for Oracle RMAN within the specific restore session.  |  | | --- | | $session = Get-VEORRMANRestoreSession  Get-VEORRMANDatabase -Session $session[0] |  Perform the following steps:   1. Run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEORRMANDatabase cmdlet. Set the $session variable as the Session parameter value and specify the necessary restore session. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Database with Specified Name

|  |  |
| --- | --- |
| This example shows how to get an Oracle database backed up with Veeam Plug-in for Oracle RMAN with the specified name.  |  | | --- | | $session = Get-VEORRMANRestoreSession  Get-VEORRMANDatabase -Session $session[0] -Name "RMAN Database" |  Perform the following steps:   1. Run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the Get-VEORRMANDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Databases with Specific Names Located in Specific Oracle Home Directories

|  |  |
| --- | --- |
| This example shows how to get Oracle databases with the specified names that are located in the specified Oracle Home directories.  |  | | --- | | $session = Get-VEORRMANRestoreSession  $dbnames = @("orcl1", "orcl2")  $oraclehomepaths = @("E:\app\administrator\product\19.3.0\dbhome\_1", "E:\app\administrator\product\19.3.0\dbhome\_2")  Get-VEORRMANDatabase -Session $session[0] -Name @dbnames -OracleHome @oraclehomepaths |  Perform the following steps:   1. Run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Declare the $dbnames variable. Assign to this variable an array with the names of the necessary Oracle databases. 2. Declare the $oraclehomepaths variable. Assign to this variable an array with the necessary Oracle Home paths. 3. Run the Get-VEORRMANDatabase cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Set the @dbnames variable as the Name parameter value. Set the @oraclehomepaths variable as the OracleHome parameter value. |

Related Commands

[Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md)


