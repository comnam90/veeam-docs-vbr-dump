---
title: "New-VBRCSVContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcsvcontainer.html"
last_updated: "1/22/2024"
product_version: "13.0.1.1071"
---

# New-VBRCSVContainer


Short Description

Creates a scope of computers listed in a CSV file.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRCSVContainer -Path <string> -MasterCredentials <CCredentials> [-NetworkCredentials <CCredentials>] [-UseCustomCredentials] [-CustomCredentials <VBRCSVCustomCredentials[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRCSVContainer](vbrcsvcontainer.md) object. This object contains a scope of computers listed in a CSV file. Use this object to create a protection group with the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path to the CSV file. The cmdlet will import computer DNS names or IP addresses from this file. | String | True | Named | True (ByValue ByProperty Name) |
| MasterCredentials | Specifies Master account credentials for authenticating with all computers listed in a CSV file.  For authenticating with computers that require different credentials, Veeam Backup & Replication uses custom credentials. If you want to use custom credentials for some computers, set the UseCustomCredentials parameter. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | True (ByProperty Name) |
| NetworkCredentials | Specifies the credentials you want to use for authenticating with the shared folder. The cmdlet will use these credentials if a CSV file is located on a file share. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |
| UseCustomCredentials | Defines that you want to use custom credentials for authenticating with some computers listed in a CSV file.  To specify custom credentials, use the CustomCredentials parameter. | SwitchParameter | False | Named | True (ByProperty Name) |
| CustomCredentials | Specifies custom credentials for authenticating with associated computers. | Accepts the [VBRCSVCustomCredentials[]](vbrcsvcustomcredentials.md) object. To get this object, run the [New-VBRCSVCustomCredentials](new-vbrcsvcustomcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCSVContainer](vbrcsvcontainer.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Scope of Computers from CSV File on Computer

|  |  |
| --- | --- |
| This example shows how to create a scope of computers from a CSV file located on your computer.  |  | | --- | | $ccreds = Get-Credential  $custom = @("172.19.51.55", "sup-v8931") | ForEach { New-VBRCSVCustomCredentials -HostName $\_ -Credentials $ccreds}  $netcreds = Get-Credential  New-VBRCSVContainer -Path "C:\Computers.csv" -MasterCredentials support\jsmith -UseCustomCredentials -CustomCredentials $custom |  Perform the following steps:   1. Specify custom credentials for computers from a CSV file:  * Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Type the credentials and save the result to the $ccreds variable. * Run the [New-VBRCSVCustomCredentials](new-vbrcsvcustomcredentials.md) cmdlet. Set the $ccreds variable as the Credentials parameter value. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $custom variable.  1. Run the New-VBRCSVContainer cmdlet. Specify the following settings:  * Specify the Path parameter value. * Specify the MasterCredentials parameter value. * Provide the UseCustomCredentials parameter value. * Set the $custom variable as the CustomCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Scope of Computers from CSV File on File Share

|  |  |
| --- | --- |
| This example shows how to create a scope of computers from a CSV file located on a file share.  |  | | --- | | $ccreds = Get-Credential  $custom = @("172.19.51.55", "sup-v8931") | ForEach { New-VBRCSVCustomCredentials -HostName $\_ -Credentials $ccreds}  $netcreds = Get-Credential  New-VBRCSVContainer -Path "//support.local/east/Computers.csv" -MasterCredentials support\jsmith -NetworkCredentials $netcreds -UseCustomCredentials -CustomCredentials $custom |  Perform the following steps:   1. Specify custom credentials for computers from a CSV file:  * Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Type the credentials and save the result to the $ccreds variable. * Run the [New-VBRCSVCustomCredentials](new-vbrcsvcustomcredentials.md) cmdlet. Set the $ccreds variable as the Credentials parameter value. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $custom variable.  1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet to create a credential object you want to use for authenticating with the shared folder. Type the credentials and save the result to the $netcreds variable. 2. Run the New-VBRCSVContainer cmdlet. Specify the following settings:  * Specify the Path parameter value. * Specify the MasterCredentials parameter value. * Set the $netcreds variable as the NetworkCredentials parameter value. * Provide the UseCustomCredentials parameter value. * Set the $custom variable as the CustomCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Protection Group with Scope of Computers from CSV File on File Share

|  |  |
| --- | --- |
| This example shows how to create a protection group with a scope of computers from a CSV file.  |  | | --- | | $ccreds = Get-Credential  $custom = @("172.19.51.55", "sup-v8931") | ForEach { New-VBRCSVCustomCredentials -HostName $\_ -Credentials $ccreds}  $netcreds = Get-Credential  $csvscope = New-VBRCSVContainer -Path "//support.local/east/Computers.csv" -MasterCredentials support\jsmith -NetworkCredentials $netcreds -UseCustomCredentials -CustomCredentials $custom  Add-VBRProtectionGroup -Name "CSV" -Container $csvscope |  Perform the following steps:   1. Specify custom credentials for computers from a CSV file:  * Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Type the credentials and save the result to the $ccreds variable. * Run the [New-VBRCSVCustomCredentials](new-vbrcsvcustomcredentials.md) cmdlet. Set the $ccreds variable as the Credentials parameter value. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $custom variable.  1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet to create a credential object you want to use for authenticating with the shared folder. Type the credentials and save the result to the $netcreds variable. 2. Run the New-VBRCSVContainer cmdlet. Specify the Path and the MasterCredentials parameter values. Set the $netcreds variable as the NetworkCredentials parameter value. Provide the UseCustomCredentials parameter value. Set the $custom variable as the CustomCredentials parameter value. Save the result to the $csvscope variable. 3. Create a protection group. To do this, run the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Set the $csvscope variable as the Container parameter value. |

Related Commands

* [New-VBRCSVCustomCredentials](new-vbrcsvcustomcredentials.md)
* [Add-VBRProtectionGroup](add-vbrprotectiongroup.md)


