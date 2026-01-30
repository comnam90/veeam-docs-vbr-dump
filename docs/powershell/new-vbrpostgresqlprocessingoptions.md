---
title: "New-VBRPostgreSQLProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrpostgresqlprocessingoptions.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRPostgreSQLProcessingOptions


Short Description

Defines settings for processing backed-up PostgreSQL databases on Linux computers.

Applies to:

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRPostgreSQLProcessingOptions [-Credentials <CCredentials>] [-UserType <VBRPostgreSQLUserType>] [-EnableArchiveLogBackup] [-ArchiveLogBackupPeriod <Int32>] [-ArchiveLogRetainAction <VBRLogRetainAction>] [-ArchiveLogRetainPeriod <Int32>] [-ArchiveLogBackupStorage <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to Veeam Agent jobs that back up Linux computers.

This cmdlet creates the VBRPostgreSQLProcessingOptions object. This object contains settings for processing backed-up PostgreSQL databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies the PostgreSQL credentials that Veeam Agent will use to connect to the PostgreSQL server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| UserType | Specifies the PostgreSQL authentication options. You can specify either of the following types of authentication options:   * DBUserWithPassword: use this option for the password-based authentication. Veeam Agent will use the database login and password to authenticate against the PostgreSQL server. * DBUserWithPasswordFile: use this option to authenticate against the PostgreSQL server with the password file. This password file must contain the user name and the password of the database user. * SystemUserWithoutPassword: use this option for the peer authentication method. Veeam Agent will use the OS user name to authenticate against the PostgreSQL server. | VBRPostgreSQLUserType | False | Named | False |
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

Defining Settings for Processing Backed-up PostgreSQL Databases

This example shows how to define settings for processing backed-up PostgreSQL databases.

|  |
| --- |
| $creds = Get-VBRCredentials -Name \*Administrator\*  New-VBRPostgreSQLProcessingOptions -Credentials $creds |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable.
2. Run the New-VBRPostgreSQLProcessingOptions cmdlet. Set the $creds variable as the Credentials parameter value.

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


