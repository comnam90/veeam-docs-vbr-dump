---
title: "Set-VBRSureBackupTestScript"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackuptestscript.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupTestScript


Short Description

Modifies settings of custom recovery verification scripts for VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupTestScript -Script <VBRCustomSureBackupTestScript> [-Name <string>] [-Path <string>] [-Argument <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of custom recovery verification scripts for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Script | Specifies a script. The cmdlet will modify settings of this script. | Accepts the VBRCustomSureBackupTestScript object. To creates this object, run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies a name for a script. The cmdlet will modify a name of the script to the specified. | String | False | Named | False |
| Path | Specifies a path to a script. The cmdlet will use this path to access the script. | String | False | Named | False |
| Argument | Specifies an IP address and the port number. The cmdlet will use this IP address and port to access the VM. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupTestScript object that defines recovery verification scripts for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Path to Custom Recovery Verification Script

|  |  |
| --- | --- |
| This example shows how to modify a path to a custom script. The cmdlet will use the C:\scripts\script.bat path instead of the C:\scripts\verificationscript.bat to access the script.  |  | | --- | | $script = New-VBRSureBackupTestScript -Name "ScriptVerification" -Path "C:\scripts\verificationscript.bat" -Argument "192.0.2.5 53"  Set-VBRSureBackupTestScript -Script $script -Path "C:\scripts\script.bat" |  Perform the following steps:   1. Run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. Specify the Name, Path and Argument parameter values. Save the result to the $script variable. 2. Run the Set-VBRSureBackupTestScript cmdlet. Set the $script variable as the Script parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying IP Address and Port Number of Custom Recovery Verification Script

|  |  |
| --- | --- |
| This example shows how to modify a path to a custom script. The cmdlet will use the 192.0.2.7 IP address and the 64 port number to access the VM.  |  | | --- | | $script = New-VBRSureBackupTestScript -Name "ScriptVerification"  -Path "C:\scripts\pre-script.bat" -Argument "192.0.2.7 75"  Set-VBRSureBackupTestScript -Script $script -Argument "192.0.2.7 64" |  Perform the following steps:   1. Run the [New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md) cmdlet. Specify the Name, Path and Argument parameter values. Save the result to the $script variable. 2. Run the Set-VBRSureBackupTestScript cmdlet. Set the $script variable as the Script parameter value. Specify the Argument parameter value. |

Related Commands

[New-VBRSureBackupTestScript](new-vbrsurebackuptestscript.md)


