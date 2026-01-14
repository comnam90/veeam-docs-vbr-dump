---
title: "Set-VBRCloudProvider"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudprovider.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudProvider

In this article

Short Description

Modifies service providers.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudProvider -CloudProvider <VBRCloudProvider> [-Address <string>] [-Description <string>] [-Port <int32>] [-Credentials <VBRCloudProviderCredentials>] [-PassThru] [-Appliance <VBRCloudProviderNetworkAppliance[]>] [-VerifyCertificate] [-CertificateThumbprint <string>] [-InstallManagementAgent] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of service provider added to Veeam Backup & Replication.

|  |
| --- |
| Important |
| The CCredentials object for the Credentials parameter is not accepted any longer. Run the [Add-VBRCloudProviderCredentials](add-vbrcloudprovidercredentials.md) cmdlet to specify the cloud provider credentials records. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudProvider | Specifies the service provider you want to modify. | Accepts the [VBRCloudProvider](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | True | Named | True (ByValue, |
| Address | Specifies a full DNS name or an IP address of the cloud gateway configured on the service provider side. | String | False | Named | False |
| Description | Specifies the description of the service provider. | String | False | Named | False |
| Port | Specifies the port over which the Veeam backup server of the user will communicate with the cloud gateway.  Permitted values: 1 to 65535.  Default: 6180. | Int32 | False | Named | False |
| Credentials | Specifies credentials for the user account registered on the service provider Veeam backup server. | Accepts the VBRCloudProviderCredentials object. To get this object, run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. | False | Named | False |
| Appliance | Specifies the appliance on the user side that will be used for the partial failover. | Accepts the [VBRHvCloudProviderNetworkAppliance[]](vbrhvcloudprovidernetworkappliance.md) object. To get this object, run the [Set-VBRCloudProviderNetworkAppliance](set-vbrcloudprovidernetworkappliance.md) cmdlet. | False | Named | False |
| VerifyCertificate | Defines if the TLS certificate must be verified by the thumbprints.  Use the CertificateThumbprint parameter to set the thumbprint that will be compared to the TLS certificate thumbprint. | SwitchParameter | False | Named | False |
| CertificateThumbprint | Specifies the thumbprint that will be compared to the TLS certificate thumbprint. | String | False | Named | False |
| InstallManagementAgent | Defines that the service provider must manage the Veeam backup server under the Backup as a Service agreement.  The cmdlet will install the Veeam Managed Backup Portal agent on the Veeam backup server. | SwitchParameter | False | Named | False |
| Force | Defines that the command will skip the certificate verification if the verification fails. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command will return the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudProvider](vbrcloudprovider.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling TLS Certificate Verification for Service Provider [Using Variable]

|  |  |
| --- | --- |
| This example shows how to enable the TLS certificate verification for a service provider.  |  | | --- | | $CloudProvider = Get-VBRCloudProvider -Name "104.45.95.227"  Set-VBRCloudProvider -CloudProvider $CloudProvider -VerifyCertificate -CertificateThumbprint "‎e6 c0 e5 1a db 73 0c 13 b3 c3 74 d4 ee 93 ab d0 08 3f 7a a8" |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $CloudProvider variable. 2. Run the Set-VBRCloudProvider cmdlet. Set the $CloudProvider variable as the CloudProvider parameter value. Provide the VerifyCertificate parameter. Specify the CertificateThumbprint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Cloud Gateway Port [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set the cloud gateway port to the default value.  |  | | --- | | Get-VBRCloudProvider -Name "104.45.95.227" | Set-VBRCloudProvider -Port 6180 |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRCloudProvider cmdlet. Specify the Port parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Configuring Network Extension Appliance of Service Provider [Using Variable]

|  |  |
| --- | --- |
| This example shows how to edit configuration of the network extension appliance configured for the service provider.  |  | | --- | | $provider = Get-VBRCloudProvider –Name "104.45.95.227"  $viAppl = Get-VBRCloudProviderNetworkAppliance -CloudProvider $provider  $newFolder = “C:\Users\admin”  $newAppliance = Set-VBRCloudProviderNetworkAppliance –NetworkAppliance $hvAppl –Folder $newFolder  $CloudProvider = Get-VBRCloudProvider -Name "104.45.95.227"  Set-VBRCloudProvider -CloudProvider $CloudProvider -Appliance $newAppliance |  Perform the following steps:   1. Modify the network extension appliance:  * Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter values. Save the result to the $provider variable. * Run the [Get-VBRCloudProviderNetworkAppliance](get-vbrcloudprovidernetworkappliance.md) cmdlet. Set the $provider variable as the CloudProvider parameter value. Save the result to the $viAppl variable. * Assign the $newFolder variable the C:\Users\admin value. * Run the [Set-VBRCloudProviderNetworkAppliance](set-vbrcloudprovidernetworkappliance.md) cmdlet for instructions. Specify the NetworkAppliance and Folder parameter values. Save the result to the $newAppliance variable.  1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $CloudProvider variable.  1. Run the Set-VBRCloudProvider cmdlet. Set the $CloudProvider variable as the CloudProvider parameter value. Set the $newAppliance variable as the Appliance parameter value. |

Related Commands

* [Set-VBRCloudProviderNetworkAppliance](set-vbrcloudprovidernetworkappliance.md)
* [Get-VBRCloudProvider](get-vbrcloudprovider.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
