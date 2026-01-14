---
title: "Set-VBRCSVContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcsvcontainer.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRCSVContainer

In this article

Short Description

Modifies a scope of computers listed in a CSV file.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCSVContainer -Container <VBRCSVContainer> [-Path <string>] [-NetworkCredentials <CCredentials>] [-MasterCredentials <CCredentials>] [-UseCustomCredentials] [-CustomCredentials <VBRCSVCustomCredentials[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRCSVContainer](vbrcsvcontainer.md) object. This object contains the scope of computers you want to add to a protection group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies the scope of computers that are listed in a CSV file. | Accepts the [VBRCSVContainer](vbrcsvcontainer.md) object. To get this object, run the [New-VBRCSVContainer](new-vbrcsvcontainer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Path | Specifies the path to the CSV file. The cmdlet will import computers' DNS names or IP addresses from this file. | String | False | Named | True (ByProperty Name) |
| MasterCredentials | Specifies Master account credentials for authenticating with all computers listed in a CSV file.  For authenticating with computers that require different credentials, Veeam Backup & Replication uses custom credentials. If you want to use custom credentials for some computers, set the UseCustomCredentials parameter. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |
| NetworkCredentials | Specifies the credentials you want to use for authenticating with the shared folder. The cmdlet will use these credentials if a CSV file is located on a file share. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |
| UseCustomCredentials | Defines that you want to use custom credentials for authenticating with some computers listed in a CSV file.  To specify custom credentials, use the CustomCredentials parameter. | SwitchParameter | False | Named | True (ByProperty Name) |
| CustomCredentials | Specifies custom credentials for authenticating with associated computers. | Accepts the [VBRCSVCustomCredentials[]](vbrcsvcustomcredentials.md) object. To get this object, run the [New-VBRCSVCustomCredentials](new-vbrcsvcustomcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCSVContainer](vbrcsvcontainer.md)

Examples

Changing Master Account Credentials for Protection Group

This example shows how to change Master account credentials for a protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Support PG"  $csv = $group.Container  $newcsv = Set-VBRCSVContainer -Container $csv -MasterCredentials "supporteast\dstones"  Set-VBRProtectionGroup -ProtectionGroup $group -Container $newcsv |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Get the protection scope. Use the Container property of the $group variable. Save the result to the $csv variable.
3. Run the Set-VBRCSVContainer cmdlet. Set the $csv variable as the Container parameter value. Specify the MasterCredentials parameter value. Save the result to the $newcsv variable.
4. Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $newcsv variable as the Container parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
