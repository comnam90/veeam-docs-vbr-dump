---
title: "Set-VBRPostgreSQLProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrpostgresqlprocessingoptions.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRPostgreSQLProcessingOptions


Short Description

Modifies settings for processing backed-up PostgreSQL databases on Linux computers.

Applies to:

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRPostgreSQLProcessingOptions -Options <VBRPostgreSQLProcessingOptions> [-Credentials <CCredentials>] [-UserType <VBRPostgreSQLUserType>] [-EnableArchiveLogBackup] [-ArchiveLogBackupPeriod <Int32>] [-ArchiveLogRetainAction <VBRLogRetainAction>] [-ArchiveLogRetainPeriod <Int32>] [-ArchiveLogBackupStorage <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for processing backed-up PostgreSQL database for Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies settings for backed-up PostgreSQL database. The cmdlet will modify these settings. | Accepts the VBRPostgreSQLProcessingOptions object. To create this object, run the [New-VBRPostgreSQLProcessingOptions](new-vbrpostgresqlprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| Credentials | Specifies the PostgreSQL credentials that Veeam Agent will use to connect to the PostgreSQL server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| UserType | Specifies the PostgreSQL authentication options. You can specify either of the following types of authentication options:   * DBUserWithPassword: use this option for the password-based authentication. Veeam Agent will use the database login and password to authenticate against the PostgreSQL server. * DBUserWithPasswordFile: use this option to authenticate against the PostgreSQL server with the password file. This password file must contain the user name and the password of the database user. * SystemUserWithoutPassword: use this option for the peer authentication method. Veeam Agent will use the OS user name to authenticate against the PostgreSQL server.   Default: DBUserWithPassword. | VBRPostgreSQLUserType | False | Named | False |
| EnableArchiveLogBackup | Defines that the cmdlet will back up WAL files. | SwitchParameter | False | Named | False |
| ArchiveLogBackupPeriod | Specifies how often in minutes the cmdlet will back up WAL files.  Default: 15 minutes. | Int32 | False | Named | False |
| ArchiveLogRetainAction | Specifies retention policy for WAL files stored in the backup location.   * WaitForBackupDeletion: use this option to keep WAL files backups the same period as image-level backups. * KeepOnlyLastDays: use this option to keep WAL files backups for a specific number of days. Use the ArchiveLogRetainPeriod parameter to specify the number of days. | VBRLogRetainAction | False | Named | False |
| ArchiveLogRetainPeriod | Specifies the number of days to keep WAL files.  Default: 15. | Int32 | False | Named | False |
| ArchiveLogBackupStorage | For Linux machines.  Specify a path to a location where WAL files are stored. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRPostgreSQLProcessingOptions object that contains settings for processing backed-up PostgreSQL databases.

Examples

Modifying PostgreSQL Authentication Options

This example shows how to modify the PostgreSQL authentication options. Veeam Agent will use the peer authentication option.

|  |
| --- |
| $options = New-VBRPostgreSQLProcessingOptions  Set-VBRPostgreSQLProcessingOptions -Options $options -UserType SystemUserWithoutPassword |

Perform the following steps:

1. Run the [New-VBRPostgreSQLProcessingOptions](new-vbrpostgresqlprocessingoptions.md) cmdlet. Save the result to the $options variable.
2. Run the Set-VBRPostgreSQLProcessingOptions cmdlet. Set the $options variable as the Options parameter value. Set the SystemUserWithoutPassword option for the UserType parameter.

Related Commands

[New-VBRPostgreSQLProcessingOptions](new-vbrpostgresqlprocessingoptions.md)


