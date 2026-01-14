---
title: "New-VBRMongoDBCustomCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmongodbcustomcredentials.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New-VBRMongoDBCustomCredentials

In this article

Short Description

Creates custom credentials for computers within MongoDB replica sets to be selected for backup operations.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Specify credentials by username and password.

|  |
| --- |
| New-VBRMongoDBCustomCredentials -Computer <VBRMongoDBComputer> -Credentials <CCredentials> [-Endpoint <String>]  [<CommonParameters>] |

* Specify credentials by using temporary certificates.

|  |
| --- |
| New-VBRMongoDBCustomCredentials -Computer <VBRMongoDBComputer> [-UseTemporaryCertificate] [-Endpoint <String>]  [<CommonParameters>] |

* Specify credentials by using temporary credentials.

|  |
| --- |
| New-VBRMongoDBCustomCredentials -Computer <VBRMongoDBComputer> [-Endpoint <String>] [-SSHElevateToRoot] [-SSHFailoverToSu] -SSHPassword <String> [-SSHPort <27017>] [-SSHRootPassword <String>] -SSHTempCredentials -SSHUser <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates custom credentials and temporary certificates for computers included in specific MongoDB replica sets.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Computer | Specifies the computer whose credentials or temporary certificate you want to create. | Accepts the [VBRMongoDBComputer](vbrmongodbcomputer.md) object. To get this object, run the [Get-VBRMongoDBComputer](get-vbrmongodbcomputer.md) cmdlet. | True | Named | True (ByPropertyName) |
| Credentials | Specifies the credentials you want to set for individual computers. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | True (ByPropertyName) |
| Endpoint | Specifies the DNS name or an IP address of the computer that is part of the MongoDB replica set. | String | False | Named | True (ByPropertyName, ByValue) |
| UseTemporaryCertificate | Specifies a temporary certificate you want to set for individual computers. Use this parameter to set a temporary certificate to use instead of custom credentials.  Note: This parameter is required only if you do not use the Credentials parameter. | SwitchParameter | True | Named | True (ByPropertyName) |
| SSHPassword | Specifies the password you want to use to authenticate against individual computers in a protection group. | String | True | Named | True (ByPropertyName) |
| SSHUser | Specifies the user name you want to use to authenticate against individual computers in a protection group. | String | True | Named | True (ByPropertyName) |
| SSHTempCredentials | Defines that the cmdlet will use single-use credentials to access Linux-based machines. | SwitchParameter | True | Named | True (ByPropertyName) |
| SSHElevateToRoot | Defines that the cmdlet will grant the non-root users with root account privileges. | SwitchParameter | False | Named | True (ByPropertyName) |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails. | SwitchParameter | False | Named | True (ByPropertyName) |
| SSHPort | Specifies the port number over which Veeam Backup & Replication communicates with the MongoDB replica set. By default, Veeam Backup & Replication uses port 27017. | Int32 | False | Named | True (ByPropertyName) |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBCustomCredentials](vbrmongodbcustomcredentials.md#VBRMongoDBCustomCredentials) object.

Examples

Configuring Custom Credentials and Temporary Certificate for Computers within Replica Sets

This command configures two individual computers within a replica set. The first is set up with custom credentials and the second is set up with a temporary certificate instead of custom credentials.

|  |
| --- |
| $computer0CustomCredentials = New-VBRMongoDBCustomCredentials -Computer $rs1Computers[0] -Credentials $computer0OsCredentials  $computer1CustomCredentials = New-VBRMongoDBCustomCredentials -Computer $rs2Computers[0] -UseTemporaryCertificate |

Perform the following steps:

1. Run the New-VBRMongoDBCustomCredentials cmdlet.

* Specify the Computer parameter value with the name of a specific computer within the replica set.
* Specify the Credentials parameter with the custom credentials you want to use.
* Save the result to the $computer0CustomCredentials variable.

1. Run the New-VBRMongoDBCustomCredentials cmdlet.

* Specify the Computer parameter value with the name of a specific computer within the replica set.
* Use the UseTemporaryCertificate parameter to use a temporary certificate instead of custom credentials.
* Save the result to the $computer1CustomCredentials variable.

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
