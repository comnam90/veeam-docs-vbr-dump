---
title: "New-VBRMongoDBDeployment"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmongodbdeployment.html"
last_updated: "9/16/2025"
product_version: "13.0.1.1071"
---

# New-VBRMongoDBDeployment

In this article

Short Description

Connects to and adds MongoDB replica sets to protection groups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Authenticate with a set of user name and password.

|  |
| --- |
| New-VBRMongoDBDeployment -HostName <String> -Port <Int32> -Credentials <CCredentials> [-UseTls]  [<CommonParameters>] |

* Authenticate with a combination of credentials, CA certificate, client certificate and client certificate password.

|  |
| --- |
| New-VBRMongoDBDeployment -HostName <String> -Port <Int32> -Credentials <CInternalCredentials> [-UseTls] [-ClientCertificatePath <String>] [-ClientCertificatePassword <String>] [-CACertificatePath <String>]  [<CommonParameters>] |

* Authenticate with a combination of CA certificate, client certificate and client certificate password.

|  |
| --- |
| New-VBRMongoDBDeployment -HostName <String> -Port <Int32> [-UseTls] -ClientCertificatePath <String> [-ClientCertificatePassword <String>] [-CACertificatePath <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet discovers replica sets using a single MongoDB daemon within the deployed MongoDB aplication.

Keep in mind the following requirements:

* You must input a host name, TCP port and valid credentials for the MongoDB application admin database.
* The MongoDB application user must have the backup role.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HostName | Specifies the DNS name or an IP address of the computer that you want to use within the MongoDB application protection group.  Note: Keep in mind that the MongoDB application host list becomes a template for the MongoHosts list for the UI. You can manually select which hosts should be included in the pool group. After that, you can use Linux root access credentials to automatically deploy Veeam Agent for Linux on the selected hosts. | String | True | Named | False |
| Port | Specifies the port number over which Veeam Backup & Replication communicates with the MongoDB replica set. By default, Veeam Backup & Replication uses port 27017. | Int32 | True | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the MongoDB replica set. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| ClientCertificatePath | Specifies the folder path to a client certificate. Use this parameter for mTLS and x509 authentication methods. | String | True for ClientCertificateSetName parameter set.  False for SecureCredentials parameter set. | Named | True (ByPropertyName) |
| ClientCertificatePassword | Specifies the password for a client certificate. | String | False | Named | True (ByPropertyName) |
| CACertificatePath | Specifies the folder path to the CA certificate. Use this parameter to verify MongoDB server certificates. | String | False |  |  |
| UseTls | Specifies the use of the TLS certificate to secure the TLS connection between the Veeam infrastructure and MongoDB deployment. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRMongoDBDeployment](vbrmongodbdeployment.md#VBRMongoDBDeployment)

Examples

Replica Set Connection and Data Loading

This example shows how to connect to a replica set and load the data from it.

|  |
| --- |
| $mongoCredentials1 = Get-VBRCredentials -Name "admin"  $replicaSet1 = New-VBRMongoDBDeployment -HostName host01 -Credentials $mongoCredentials1 -Port 27017 |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter with the user account you want to connect with. Save the result to the $mongoCredentials1 variable.
2. Run the New-VBRMongoDBDeployment cmdlet.

* Specify the HostName parameter with the DNS name or IP address of the computer within the replica set.
* Specify the Credentials parameter with the $mongoCredentials1 variable.
* Specify the Port parameter with the port number 27017.

Related Command

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 9/16/2025

Page content applies to build 13.0.1.1071
