---
title: "New-VBROracleRMANProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbroraclermanprocessingoptions.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New-VBROracleRMANProcessingOptions

In this article

Short Description

Creates the Oracle RMAN database processing settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBROracleRMANProcessingOptions -Credentials <CCredentials> [-AuthenticationMode {OSAuth | SplitAuth}] [-DBCredentials <DBCredentials>] [-ArchivedLogAction {Keep | Delete}] [-ArchiveLogBackupPeriod <int>] [-ParallelChannelsCount <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Oracle RMAN.

This cmdlet creates Oracle RMAN database processing settings. You can set up the following options:

* The type of authentication to connect to Oracle RMAN hosts and databases.
* The way Veeam Backup & Replication will process archived logs.
* Schedule settings for archived logs processing.
* Number of data channels to back up archived logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies the credentials for Oracle RMAN database processing. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| AuthenticationMode | Specifies the authentication method to connect to Oracle RMAN hosts and databases:   * OSAuth: use this option to connect to the Oracle host and to the database using OS authentication. * SplitAuth: use this option if you want to use the OS and database credentials simultaneously to connect to the Oracle host and database. | [VBRApplicationBackupAuthenticationMode](enums.md#VBRApplicationBackupAuthenticationMode) | False | Named | False |
| DBCredentials | Specifies the database credentials.  Note: This parameter is required only when using the AuthenticationMode parameter with the SplitAuth option. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ArchivedLogAction | Specifies the way of database processing:   * Keep: to keep archived logs that were backed up. * Delete: to delete archived logs that were backed up. | VBROracleRMANArchivedLogAction | False | Named | False |
| ArchiveLogBackupPeriod | Specifies the integer defining the frequency for archived logs backup in minutes.  Permitted values: 5 to 480. | Int32 | False | Named | False |
| ParallelChannelsCount | Specifies the integer defining the number of data channels that can be assigned. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBROracleRMANOptions object that defines Oracle RMAN database processing settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Oracle RMAN Database Processing Settings for Application Backup Policies for Veeam Plug-In for Oracle RMAN

|  |  |
| --- | --- |
| This example shows how to create an Oracle RMAN database processing settings for application backup policies for Veeam Plug-In for Oracle RMAN. The policy will back up archived logs every 15 minutes and send application backups to the target storage using 3 parallel data channels.  |  | | --- | | $db\_administrator = Get-VBRCredentials -Name dboracle  New-VBROracleRMANProcessingOptions -Credentials $db\_administrator -ArchivedLogAction Keep -ArchiveLogBackupPeriod 15 -ParallelChannelsCount 3 |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value with the account user name. Save the result to the $db\_administrator variable. 2. Run the New-VBROracleRMANProcessingOptions cmdlet. Specify the following settings:  * Set the $db\_administrator variable as the Credentials parameter value. * Set the Keep option for the ArchivedLogAction parameter. * Specify the ArchiveLogBackupPeriod parameter value. * Specify the ParallelChannelsCount parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Using OS Authentication to access the Oracle Host and RMAN Database

|  |  |
| --- | --- |
| This example shows how to connect to the Oracle host and database using the OS authentication method and credentials.  |  | | --- | | $creds = Get-VBRCredentials -Name oracle  New-VBROracleRMANProcessingOptions -AuthenticationMode OSAuth -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value with the account user name on the host. The cmdlet will return credentials with this name. Save the result to the $creds variable. 2. Run the New-VBROracleRMANProcessingOptions cmdlet. Specify the following settings:  * Set the OSAuth option for the AuthenticationMode parameter. * Set the $creds variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Using OS and Database Authentication to access the Oracle Host and RMAN Database

|  |  |
| --- | --- |
| This example shows how to connect to the Oracle host and database using the OS and database authentication methods and credentials simultaneously.  |  | | --- | | $creds = Get-VBRCredentials -Name oraclehost  $dbcreds = Get-VBRCredentials -Name dboracle  New-VBROracleRMANProcessingOptions -AuthenticationMode SplitAuth -Credentials $creds -DBCredentials $dbcreds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value with the host account user name. The cmdlet will return credentials with this name. Save the result to the $creds variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value with the database account user name. The cmdlet will return credentials with this name. Save the result to the $dbcreds variable. 3. Run the New-VBROracleRMANProcessingOptions cmdlet. Specify the following settings:  * Set the SplitAuth option for the AuthenticationMode parameter. * Set the $creds variable as the Credentials parameter value. * Set the $dbcreds variable as the DBCredentials parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
