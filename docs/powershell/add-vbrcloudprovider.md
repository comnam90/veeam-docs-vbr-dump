---
title: "Add-VBRCloudProvider"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudprovider.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudProvider


Short Description

Adds cloud service providers.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCloudProvider -Address <string> -Credentials <VBRCloudProviderCredentials> [-Description <string>] [-Port <int32>] [-Appliance <VBRCloudProviderNetworkAppliance[]>] [-VerifyCertificate] [-CertificateThumbprint <string>] [-InstallManagementAgent] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a new service provider to Veeam Backup & Replication.

You can add several providers using one cloud gateway to your Veeam backup console. The provider credentials must have different user names.

You must set a network extension appliance if you plan to replicate your VMs to the cloud. Pre-configure the network extension appliance in advance. For details, see [Network Appliance](user_network_appliance.md).

|  |
| --- |
| Important |
| The CCredentials type object for the Credentials parameter is not accepted any longer. Run the [Add-VBRCloudProviderCredentials](add-vbrcloudprovidercredentials.md) cmdlet to specify the cloud provider credentials records. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Address | Specifies a full DNS name or IP address of the cloud gateway configured on the service provider side. | String | True | Named | False |
| Description | Specifies the description of the service provider. | String | False | Named | False |
| Port | Specifies the port over which user’s Veeam backup server will communicate with the cloud gateway.  Permitted values: 1 to 65535.  Default: 6180. | Int32 | False | Named | False |
| Credentials | Specifies credentials for the user account registered on the service provider Veeam backup server. | Accepts the VBRCloudProviderCredentials object. To get this object, run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. | True | Named | False |
| Appliance | Specifies the network extension appliance on the user side.  You must configure a network extension appliance if you want to replicate to the cloud. | Accepts the [VBRHvCloudProviderNetworkAppliance[]](vbrhvcloudprovidernetworkappliance.md) object. To get this object, run the [New-VBRCloudProviderNetworkAppliance](new-vbrcloudprovidernetworkappliance.md) cmdlet. | False | Named | False |
| VerifyCertificate | Defines if the TLS certificate must be verified by the thumbprints.  Use the CertificateThumbprint parameter to set the thumbprint that will be compared to the TLS certificate thumbprint. | SwitchParameter | False | Named | False |
| CertificateThumbprint | Specifies the thumbprint that will be compared to the TLS certificate thumbprint. | String | False | Named | False |
| InstallManagementAgent | Defines that the service provider must manage the Veeam backup server under the Backup as a Service agreement.  The cmdlet will install the Veeam Managed Backup Portal agent on the Veeam backup server. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will skip the certificate verification if the verification fails. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudProvider](vbrcloudprovider.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Cloud Service Provider with Default Settings

|  |  |
| --- | --- |
| This example shows how to add a cloud service provider to Veeam Backup & Replication using default settings. The service provider IP address is 198.51.100.11.  |  | | --- | | $credentials = Get-VBRCloudProviderCredentials -Name "Tenant1"  Add-VBRCloudProvider -Address "198.51.100.11" -Credentials $credentials |  Perform the following steps:   1. Run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Add-VBRCloudProvider cmdlet. Specify the Address parameter value. Set the $credentials variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Cloud Service Provider with Specific Settings

|  |  |
| --- | --- |
| This example shows how to add a cloud service provider with the following settings:   * The service provider IP address is 198.51.100.11.  * The service provider uses port 6252 for connection. * The TLS certificate thumbprint verification is enabled. The thumbprint is ‎e6 c0 e5 1a db 73 0c 13 b3 c3 74 d4 ee 93 ab d0 08 3f 7a a8.   |  | | --- | | $credentials = Get-VBRCloudProviderCredentials -Name "Tenant1"  Add-VBRCloudProvider -Address "198.51.100.11" -Description "Cloud gateway for SP" -Port 6252 -Credentials $credentials -VerifyCertificate -CertificateThumbprint "‎e6 c0 e5 1a db 73 0c 13 b3 c3 74 d4 ee 93 ab d0 08 3f 7a a8" |  Perform the following steps:   1. Run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Add-VBRCloudProvider cmdlet. Specify the following settings:  * Specify the Address and the Description parameter values. * Specify the Port parameter value. * Set the $credentials variable as the Credentials parameter value. * Provide the VerifyCertificate parameter. * Specify the CertificateThumbprint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Cloud Service Provider and Configuring Network Extension Appliance

|  |  |
| --- | --- |
| This example shows how to add a service provider and configure a network extension appliance. The service provider IP address is 198.51.100.11.  |  | | --- | | $server = Get-VBRServer –Type HvServer -Name "srv02.tech.local"  $folder = "C:\Datastore"  $network = Get-VBRHvServerNetworkInfo -Server $server  | Where { $\_.NetworkName -eq "VM Network" }  $viAppl = New-VBRCloudProviderNetworkAppliance -Server $server -Network $network –Folder $folder  $credentials = Get-VBRCloudProviderCredentials -Name "Tenant1"  Add-VBRCloudProvider -Address "198.51.100.11" -Credentials $credentials -Appliance $viAppl |  Perform the following steps:   1. Create a network extension appliance:  * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the HvServer option for the Type parameter. Specify the Name parameter value. Save the server to the $server variable. * Assign the C:\Datastore value to the $folder variable. * Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value and use the Where-Object statement to filter the networks by the .NetworkName property. Save the network to the $network variable. * Run the [New-VBRCloudProviderNetworkAppliance](new-vbrcloudprovidernetworkappliance.md) cmdlet. Specify the Server, Network and Folder parameter values. Save the result to the $viAppl variable.  1. Run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable.  1. Run the Add-VBRCloudProvider cmdlet. Specify the Address parameter value. Set the $credentials variable as the Credentials parameter value. Set the $viAppl variable as the Appliance parameter value. |

Related Commands

* [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md)
* [Get-VBRCloudProviderNetworkAppliance](get-vbrcloudprovidernetworkappliance.md)


