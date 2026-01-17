---
title: "Get-VEORRMANDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorrmandatabasefile.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# Get-VEORRMANDatabaseFile


Short Description

Returns full file names for an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORRMANDatabaseFile [-Database] <VEORRMANDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet returns full file names for an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database backed up with Veeam Plug-in for Oracle RMAN. The cmdlet will return an array of full file names for the specified database. | Accepts the [VEORRMANDatabase](veorrmandatabase.md) object. To get this object, run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORRMANDatabaseFile](veorrmandatabasefile.md)[] array that contains the full file names for the Oracle database backed up with Veeam Plug-in for Oracle RMAN.

Example

Getting List of Full File Names for Backed-Up Oracle Database

This example shows how to get a list of full file names for an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

|  |
| --- |
| $session = Get-VEORRMANRestoreSession  $database = Get-VEORRMANDatabase -Session $session[0] -Name "orclrman"  Get-VEORRMANDatabaseFile -Database $database |

Perform the following steps:

1. Run the [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Get-VEORRMANDatabaseFile cmdlet. Set the $database variable as the Database parameter value.

Related Commands

* [Get-VEORRMANRestoreSession](get-veorrmanrestoresession.md)
* [Get-VEORRMANDatabase](get-veorrmandatabase.md)


