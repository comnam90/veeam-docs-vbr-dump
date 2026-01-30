---
title: "Remove-VBRCloudPublicIP"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudpublicip.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudPublicIP


Short Description

Removes IP addresses from public IP addresses pools.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Remove-VBRCloudPublicIP -CloudIp <VBRCloudIP[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected IP address from the public IP addresses pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudIp | Specifies the array of IP addresses that you want to remove. | Accepts the [VBRCloudIP[]](vbrcloudip.md) object. To get this object, run the [Get-VBRCloudPublicIP](get-vbrcloudpublicip.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing IP Address from Pool of Public IP Addresses

|  |  |
| --- | --- |
| This example shows how to remove the first IP address from the configured pool of public IP addresses.  |  | | --- | | $ip = Get-VBRCloudPublicIP  Remove-VBRCloudPublicIP –CloudIP $ip[0] |  Perform the following steps:   1. Run the [Get-VBRCloudPublicIP](get-vbrcloudpublicip.md) cmdlet. Save the pool to the $ip variable.   Mind the ordinal number of the necessary IP address (in our example, it is the first IP address in the array).   1. Run the Remove-VBRCloudPublicIP cmdlet. Set the $ip variable as the CloudIP parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing IP Address from Pool of Public IP Addresses

|  |  |
| --- | --- |
| This example shows how to remove all IP addresses assigned to the ABC Company cloud tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant –Name "ABC Company"  $ip = Get-VBRCloudPublicIP –Tenant $tenant  Remove-VBRCloudPublicIP –CloudIP $ip |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBRCloudPublicIP](get-vbrcloudpublicip.md) cmdlet. Set the $tenant variable as the Tenant parameter value. Save the result to the $ip variable. 3. Run the Remove-VBRCloudPublicIP cmdlet. Set the $ip variable as the CloudIP parameter value. |

Related Commands

[Get-VBRCloudPublicIP](get-vbrcloudpublicip.md)


