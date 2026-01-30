---
title: "Add-VBRvCloudVC"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcloudvc.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Add-VBRvCloudVC


Short Description

Adds vCenter Server managed by Cloud Director to Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a vCenter Server managed by the Cloud Director using the user name/password scenario.

|  |
| --- |
| Add-VBRvCloudVC -vCloudServer <CHost> -VCInfo <CVcdVcInfo> -User <string> -Password <string> [-Name <string>] [-Port <int>] [-Description <string>] [-Force]  [<CommonParameters>] |

* Add a vCenter Server managed by the Cloud Director using the credentials scenario.

|  |
| --- |
| Add-VBRvCloudVC -vCloudServer <CHost> -VCInfo <CVcdVcInfo> -Credentials <CCredentials> [-Name <string>] [-Port <int>] [-Description <string>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a new vCenter Server to Veeam Backup & Replication infrastructure. The vCenter Server is registered as a part of Cloud Director.

|  |
| --- |
| ![Add-VBRvCloudVC](images/icon_note.webp) Note: |
| Run the [Add-VBRvCloud](add-vbrvcloud.md) cmdlet to add a Cloud Director server to Veeam Backup & Replication infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| vCloudServer | Specifies the Cloud Director server you want to connect a vCenter to. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 0 | True (ByValue, |
| VCInfo | Specifies the vCenter Server you want to connect to the Cloud Director. | Accepts the CVcdVcInfo object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | 1 | False |
| User | Specifies the user name you want to use for authenticating with the vCenter Server.  If you use the User/Password scenario, the Credentials parameter must be omitted. | String | True | 2 | False |
| Password | Specifies the password you want to use for authenticating with the vCenter Server.  If you use the User/Password scenario, the Credentials parameter must be omitted. | String | True | 3 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the vCenter Server.  If you use the Credentials scenario, the User and Password parameters must be omitted. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Name | Specifies the DNS name or IP address of the vCenter Server you want to connect. | String | False | Named | False |
| Port | Specifies the web-service port number. If not set, the default port number 443 will be used.  Note: When you customize the port number, you must set this port on the vCenter Server/ESXi host settings first. | Int | False | Named | False |
| Description | Specifies the description of the vCenter Server. If not set, the default description containing the user name of the user who created the record and date and time of creation will be used. | String | False | Named | False |
| Force | Defines that the cmdlet will add a vCenter Server without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CHost

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding vCenter Server with User Name and Password [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to add a new vCenter Server with the following parameters:   * The vCenter will be registered on the server with 172.16.1.13 IP address. * The user name is Administrator and the password is Password. * The Port parameter is not set to enable the default 443 web-service port number. * The Description parameter is not set to enable the default description.   |  | | --- | | $vc = Find-VBRvCloudEntity -Vc  Get-VBRServer -Name "172.16.1.13" | Add-VBRvCloudVC -VCInfo $vc -User "Administrator" -Password "Password" -Name "vCenter Server 1" |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the Vc parameter. Save the result to the $vc variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Add-VBRvCloudVC cmdlet. Specify the following settings:  * Set the $vc variable as the VCInfo parameter value. * Specify the User and the Password parameter values. * Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding vCenter Server with Saved Credentails [Using Variable]

|  |  |
| --- | --- |
| This command adds a new vCenter Server with the following parameters:   * The vCenter will be registered on the server with 172.16.1.13 IP address.  * The Port parameter is set to 456. * The Description parameter is not set to enable the default description.   |  | | --- | | $s = Get-VBRServer -Name "172.16.1.13"  $vc = Find-VBRvCloudEntity -Vc  $creds = Get-VBRCredentials -Name "vCenter Administrator"  Add-VBRvCloudVC -vCloudServer $s -VCInfo $vc -Credentials $creds -Name "vCenter Server 2" -Port 456 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $s variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the Vc parameter. Save the result to the $vc variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the credentials to the $creds variable. 4. Run the Add-VBRvCloudVC cmdlet. Specify the following settings:  * Set the $s variable as the vCloudServer parameter value. * Set the $vc variable as the VCInfo parameter value. * Set the $creds variable as the Credentials parameter value. * Specify the Name parameter value. * Specify the Port parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md) ([-Vc])
* [Get-VBRCredentials](get-vbrcredentials.md)


