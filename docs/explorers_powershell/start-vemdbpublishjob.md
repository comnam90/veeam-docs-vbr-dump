---
title: "Start-VEMDBPublishJob"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vemdbpublishjob.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Publishes a backed-up MongoDB instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEMDBPublishJob [-Session] <VEMDBRestoreSession> [-PublishInstancePort <Int32>] [-Server <String>] [-SshPort <Int32>] -Credential <VEMDBLinuxCredentials> [-ToPointInTimeUTC <DateTime>] [-RestoreInstancePort <Int32>] [-InstanceCredentials <PSCredential>] [-UseTLS] [-UseSystemCertificateAuthority] [-CertificateAuthorityPemFilePath <String>] [-UseX509Authentication] [-ClientCertificateAndKeyPemFilePath <String>] [-ClientKeyPassword <SecureString>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet publishes a backed-up MongoDB instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session initiated to perform operations with MongoDB. | Accepts the [VEMDBRestoreSession](vemdbrestoresession.md) object. To get this object, run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| CertificateAuthorityPemFilePath | Specifies the path to the custom Certificate Authority (CA) PEM file used to verify the certificate issued to the MongoDB deployment. You can use this parameter with the UseTLS and UseX509Authentication parameters.  Note: If you use this parameter, do not specify the UseSystemCertificateAuthority parameter. | String | False | Named | False |
| ClientCertificateAndKeyPemFilePath | Specifies the path to the PEM file containing the client certificate and the related private key. You can use this parameter with the UseTLS and UseX509Authentication parameters. | String | False | Named | False |
| ClientKeyPassword | Defines the password used to decrypt the private key specified in the ClientCertificateAndKeyPemFilePath parameter. | SecureString | False | Named | False |
| Credential | Specifies credentials for authenticating to the primary node of the MongoDB deployment or the target MongoDB server.  Note: The user must have root privileges on the target server. | Accepts the [VEMDBLinuxCredentials](vemdblinuxcredentials.md) object. To get this object, run the [New-VEMDBLinuxCredentials](new-vemdblinuxcredentials.md) cmdlet. | True | Named | False |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| InstanceCredentials | Specifies the credentials for the target MongoDB instance.  Consider the following:   * The user must have the root MongoDB role on the target replica set. * Do not specify this parameter if you use the UseX509Authentication parameter. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| PublishInstancePort | Specifies a port for the published MongoDB instance. | Int32 | False | Named | False |
| RestoreInstancePort | Specifies the port of the instance to which the contents of the published MongoDB instance will be restored.  Default: 27017 | Int32 | False | Named | False |
| Server | Specifies DNS name or IP address of the primary node of the target MongoDB deployment or the target MongoDB server. | String | False | Named | False |
| SshPort | Specifies the SSH port number that the cmdlet will use to connect to the Linux machine.  Default: 22 | Int32 | False | Named | False |
| ToPointInTimeUTC | Specifies a point in time in the UTC format within the restore interval of the MongoDB instance.  The cmdlet will publish the instance to the state of the specified point in time. If you do not use this parameter, the cmdlet will restore the instance to the point in time when the restore point for which you started the restore session was created. | DateTime | False | Named | False |
| UseSystemCertificateAuthority | Defines that the cmdlet will use the Certificate Authority (CA) store of the mount server associated with the backup repository to verify the certificate issued to the MongoDB deployment. You can use this parameter with the UseTLS and UseX509Authentication parameters.  Note: If you use this parameter, do not specify the CertificateAuthorityPemFilePath parameter. | SwitchParameter | False | Named | False |
| UseTLS | Defines that the cmdlet will connect to the target MongoDB deployment using a secure TLS protocol.  Note: This parameter is obligatory if you use the UseX509Authentication parameter and optional if you use the InstanceCredentials parameter. | SwitchParameter | False | Named | False |
| UseX509Authentication | Defines that the cmdlet will use X.509 authentication to connect to the target MongoDB deployment.  Note: If you use this parameter, do not specify the InstanceCredentials parameter. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBInstancePublish](vemdbinstancepublish.md)[] array that contains information about the publishing process for the MongoDB instance.

Example

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Publishing MongoDB Instance

|  |  |
| --- | --- |
| This example shows how to publish a backed-up MongoDB instance to a machine with MongoDB. This is a temporary operation for testing or development purposes, which allows you to check the data contained in the MongoDB instance. This example uses the TLS protocol to connect to the target MongoDB deployment.  |  | | --- | | $session = Get-VEMDBRestoreSession  $instancecreds = Get-Credential  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEMDBLinuxCredentials -Account "root" -Password $securepassword  $publish = Start-VEMDBPublishJob -Session $session -InstanceCredentials $instancecreds -Credential $linuxcreds -PublishInstancePort 27018 -Server "mongodb01" -UseTLS -UseSystemCertificateAuthority |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable. The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to specify the credentials to authenticate to the MongoDB replica set. Save the result to the $instancecreds variable. 2. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 3. Run the [New-VEMDBLinuxCredentials](new-vemdblinuxcredentials.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $linuxcreds variable. 4. Run the Start-VEMDBPublishJob cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value. * Set the $instancecreds variable as the InstanceCredentials parameter value. * Set the $linuxcreds variable as the Credential parameter value. * Specify the PublishInstancePort parameter value. * Specify the Server parameter value. * Provide the UseTLS parameter. * Provide the UseSystemCertificateAuthority parameter.   Save the result to the $publish variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Publishing MongoDB Instance to Restore Collections to Point-in-Time State

|  |  |
| --- | --- |
| This example shows how to publish a backed-up MongoDB instance to a specific point-in-time state, which allows you to restore the collections contained in the instance to that point-in-time state. This example uses X.509 authentication to connect to the target MongoDB deployment.  |  | | --- | | $session = Get-VEMDBRestoreSession  $time = Get-Date -Date "2025-06-24 13:00:00"  $timeutc = $time.ToUniversalTime()  $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  $linuxcreds = New-VEMDBLinuxCredentials -Account "root" -Password $securepassword  $keypassword = Read-Host -Prompt "Enter password" -AsSecureString  $publish = Start-VEMDBPublishJob -Session $session -Credential $linuxcreds -PublishInstancePort 27018 -RestoreInstancePort 27017 -Server "mongodb01" -UseTLS -UseX509Authentication -CertificateAuthorityPemFilePath "C:\Users\Administrator\Documents\MongoDB\certs\CA.pem" -ClientCertificateAndKeyPemFilePath "C:\Users\Administrator\Documents\MongoDB\certs\client.pem" -ClientKeyPassword $keypassword |  Perform the following steps:   1. Run the [Get-VEMDBRestoreSession](get-vemdbrestoresession.md) cmdlet. Save the result to the $session variable. The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.  1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet. Specify the Date parameter value to set the point in time to which the instance must be published. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $timeutc variable. 3. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 4. Run the [New-VEMDBLinuxCredentials](new-vemdblinuxcredentials.md) cmdlet. Specify the Account parameter value. Set the $securepassword variable as the Password parameter value. Save the result to the $linuxcreds variable. 5. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $keypassword variable. 6. Run the Start-VEMDBPublishJob cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value. * Set the $linuxcreds variable as the Credential parameter value. * Specify the PublishInstancePort parameter value. * Specify the RestoreInstancePort parameter value. * Specify the Server parameter value. * Provide the UseTLS parameter.  * Provide the UseX509Authentication parameter. * Specify the CertificateAuthorityPemFilePath parameter value. * Specify the ClientCertificateAndKeyPemFilePath parameter value. * Set the $keypassword variable as the ClientKeyPassword parameter value.   Save the result to the $publish variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VEMDBRestoreSession](get-vemdbrestoresession.md)
* [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [New-VEMDBLinuxCredentials](new-vemdblinuxcredentials.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
