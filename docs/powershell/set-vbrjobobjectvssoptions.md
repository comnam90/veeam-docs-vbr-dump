---
title: "Set-VBRJobObjectVssOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobobjectvssoptions.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Set-VBRJobObjectVssOptions


Short Description

Customizes job VSS settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Apply a set of customized VSS settings to the specific objects in job.

|  |
| --- |
| Set-VBRJobObjectVssOptions -Object <CObjectInJob> -Options <CVssOptions>  [<CommonParameters>] |

* Set credentials to authenticate with the specific objects in job.

|  |
| --- |
| Set-VBRJobObjectVssOptions -Object <CObjectInJob> -Credentials <CCredentials>  [<CommonParameters>] |

Detailed Description

This cmdlet applies a set of customized VSS settings to the specific objects in job or sets credentials to authenticate with the specific objects in job.

To apply the set of customized settings you need to first create a CVssOptions object. This object unifies all the VSS options you want to apply to the job object.

Run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet to create the CVssOptions object.

Run the [Set-VBRJobVssOptions](set-vbrjobvssoptions.md) cmdlet to set the VSS options to the whole job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Object | Specifies the VMs and VM containers for which you want to change VSS settings. | Accepts the CObjectInJob object. To get this object, run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Options | Specifies the option that you want to change. | Accepts the CVssOptions object. To get this object, run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet. | True | 1 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the guest VM. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Applying Custom VSS Options to Specific VM [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to apply custom VSS options to the AD\_01 VM included in the backup job named Active Directory Backup.  |  | | --- | | $options = New-VBRJobVssOptions -ForObject  Get-VBRJob -Name "Active Directory Backup" | Get-VBRJobObject -Name "AD\_01" | Set-VBRJobObjectVssOptions -Options $options |  Perform the following steps:   1. Run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet. Provide the ForObject parameter. Save the result to the $options variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Specify the Name parameter value. 4. Pipe the cmdlet output to the Set-VBRJobObjectVssOptions cmdlet. Set the $options variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Custom VSS Options to VM Running Active Directory [Using Variable]

|  |  |
| --- | --- |
| This example shows how to apply custom VSS options to the VMs running Active Directory represented by the $AD\_VMs variable.  |  | | --- | | $AD\_VMs = Get-VBRJobObject  $options = New-VBRJobVssOptions -ForObject  Set-VBRJobObjectVssOptions -Object $AD\_VMs -Options $options |  Perform the following steps:   1. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Save the result to the $AD\_VMs variable. 2. Run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet. Provide the ForObject parameter. Save the result to the $options variable. 3. Run the Set-VBRJobObjectVssOptions cmdlet. Set the $AD\_VMs variable as the Object parameter value. Set the $options variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Setting Credentials to Authenticate with SQL Server Included in Specific Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set credentials to authenticate with the SQL server included in the SharePoint backup job.  |  | | --- | | $SharePointBackup = Get-VBRJob  $Administrator = Get-VBRCredentials  Get-VBRJobObject -Job $SharePointBackup -Name "SharePoint\_SQL" | Set-VBRJobObjectVssOptions -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $SharePointBackup variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 3. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $SharePointBackup variable as the Job parameter value. Specify the Name parameter value. 4. Pipe the cmdlet output to the Set-VBRJobObjectVssOptions cmdlet. Set the $Administrator variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Setting Credentials to Authenticate with VM [Using Variable]

|  |  |
| --- | --- |
| This example shows how to set credentials to authenticate with the VM represented by the $SharePoint\_SQL variable.  |  | | --- | | $SharePoint\_SQL = Get-VBRJobObject  $Administrator = Get-VBRCredentials  Set-VBRJobObjectVssOptions -Object $SharePoint\_SQL -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Save the result to the $SharePoint\_SQL variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 3. Run the Set-VBRJobObjectVssOptions cmdlet. Set the $SharePoint\_SQL variable as the Object parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

* [Get-VBRJobObject](get-vbrjobobject.md)
* [Get-VBRJob](get-vbrjob.md)
* [New-VBRJobVssOptions](new-vbrjobvssoptions.md) ([-ForObject])
* [Get-VBRCredentials](get-vbrcredentials.md)


