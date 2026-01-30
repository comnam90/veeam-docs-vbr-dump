---
title: "Set-VBROracleRMANProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbroraclermanprocessingoptions.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBROracleRMANProcessingOptions


Short Description

Modifies the Oracle RMAN database processing settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBROracleRMANProcessingOptions -Options <VBROracleRMANProcessingOptions> [-AuthenticationMode {OSAuth | SplitAuth}] [-Credentials <CCredentials>] [-DBCredentials <DBCredentials>] [-ArchivedLogAction {Keep | Delete}] [-ArchiveLogBackupPeriod <int>] [-ParallelChannelsCount <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Oracle RMAN.

This cmdlet modifies Oracle RMAN database processing settings. You can update the following options:

* Credentials that Veeam Backup & Replication will use to connect to the database system.

* The type of authentication to connect to Oracle RMAN hosts and databases.

* The way Veeam Backup & Replication will process archived logs.
* Schedule settings for archived logs processing.
* Number of data channels to back up archived logs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the database processing options that you plan to modify. | Accepts the VBROracleRMANProcessingOptions object. To get this object, run the [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
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

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing the Database Administrator Account Username

|  |  |
| --- | --- |
| This example shows how to modify the database administrator account username. The modified policy will send application backups to the target storage using 3 parallel data channels.  |  | | --- | | $db\_administrator = Get-VBRCredentials -Name oracle  $db\_administrator2 = Get-VBRCredentials -Name administrator  $processoptions = New-VBROracleRMANProcessingOptions -Credentials $db\_administrator -ArchivedLogAction Keep -ArchiveLogBackupPeriod 15 -ParallelChannelsCount 1  Set-VBROracleRMANProcessingOptions -Options $processoptions -Credentials $db\_administrator2 -ParallelChannelsCount 3 |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the current database account user name. Save the result to the $db\_administrator variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the new database account user name. Save the result to the $db\_administrator2 variable. 3. Run the [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) cmdlet. Set the $db\_administrator variable as the Credentials parameter value. Specify the ArchivedLogAction, ArchiveLogBackupPeriod and ParallelChannelsCount parameter values. Save the result to the $processoptions variable. 4. Run the Set-VBROracleRMANProcessingOptions cmdlet. Set the $processoptions variable as the Options parameter value. Set the $db\_administrator2 variable as the new Credentials parameter value. Specify the ParallelChannelsCount parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Using OS and Database Authentication to Access the Oracle Host and RMAN Database

|  |  |
| --- | --- |
| This example shows how to switch from OS authentication mode to the authentication mode that requires both OS and database credentials to connect to the Oracle host and database. The database credentials are required when switching the authentication mode with the SplitAuth parameter.  The Set-VBROracleRMANProcessingOptions cmdlet is used to change the current processing options.  |  | | --- | | $creds = Get-VBRCredentials -Name oracle  $rmanprocopts = New-VBROracleRMANProcessingOptions -AuthenticationMode OSAuth -Credentials $creds  $creds2 = Get-VBRCredentials -Name oraclehost  $dbcreds2 = Get-VBRCredentials -Name dboracle  $rmanprocopts2 = Set-VBROracleRMANProcessingOptions -Options $rmanprocopts -AuthenticationMode SplitAuth -DBCredentials $dbcreds2 |   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the current host account user name. The cmdlet will return credentials with this name. Save the result to the $creds variable. 2. Run the [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) cmdlet and save the result to the current processing options variable $rmanprocopts. Specify the following settings:  * Set the OSAuth option for the AuthenticationMode parameter. * Set the $creds variable as the Credentials parameter value.  1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the new host account user name. Save the result to the $creds2 variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the new database account user name. Save the result to the $dbcreds2 variable. 3. Run the Set-VBROracleRMANProcessingOptions cmdlet and save the result to the new processing options variable $rmanprocopts2 to change the current processing options $rmanprocopts. Specify the following settings:  * Set the new processing options variable $rmanprocopts for the Options parameter. * Set the $dbcreds2 variable as the DBCredentials parameter value.   Note: You do not have to specify the OS credentials if you have not made any changes previously. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Change OS Authentication Credentials to access the Oracle Host and RMAN Database

|  |  |
| --- | --- |
| This example shows how to change the OS credentials to connect to the Oracle host and database without changing the authentication method. To be able to specify the database credentials, you must use the AuthenticationMode parameter with the SplitAuth value.    The Set-VBROracleRMANProcessingOptions cmdlet is used to change the current processing options.  |  | | --- | | $creds = Get-VBRCredentials -Name oracle  $dbcreds = Get-VBRCredentials -Name dborcl  $rmanprocopts = New-VBROracleRMANProcessingOptions -AuthenticationMode SplitAuth -Credentials $creds -DBCredentials $dbcreds  $creds2 = Get-VBRCredentials -Name oraclehost  $dbcreds2 = Get-VBRCredentials -Name dboracle1  $rmanprocopts2 = Set-VBROracleRMANProcessingOptions -Options $rmanprocopts -AuthenticationMode SplitAuth -Credentials $creds2 -DBCredentials $dbcreds2 |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the current host account user name. The cmdlet will return credentials with this name. Save the result to the $creds variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the current database account user name. The cmdlet will return credentials with this name. Save the result to the $dbcreds variable. 3. Run the [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) cmdlet and save the result to the current processing options variable. Specify the following settings:  * Set the SplitAuth option for the AuthenticationMode parameter. * Set the $creds variable as the Credentials parameter value. * Set the $dbcreds variable as the DBCredentials parameter value.  1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the new host account user name. Save the result to the $creds2 variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the new database account user name. Save the result to the $dbcreds2 variable. 3. Run the Set-VBROracleRMANProcessingOptions cmdlet and save the result to the new processing options variable to change the current processing options. Specify the following settings:  * Set the new processing options variable for the Options parameter. * Set the $creds2 variable as the new Credentials parameter value. * Set the $dbcreds2 variable as the DBCredentials parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md)


