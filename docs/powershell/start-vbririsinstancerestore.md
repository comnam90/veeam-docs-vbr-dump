---
title: "Start-VBRIrisInstanceRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbririsinstancerestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRIrisInstanceRestore


Short Description

Starts restore of InterSystems IRIS instances.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore the InterSystems IRIS instance to its original location. This is the default restore operation.

|  |
| --- |
| Start-VBRIrisInstanceRestore -RestorePoint <Object> [-PathMapping <VBRIrisInstancePathMappingRule[]>] [-Force] [-RunAsync]  [<CommonParameters>] |

* Restore the InterSystems IRIS instance to another server.

|  |
| --- |
| Start-VBRIrisInstanceRestore -RestorePoint <Object> -ServerName <String> -ServerCredentials <CCredentials> [-PathMapping <VBRIrisInstancePathMappingRule[]>] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restore of an InterSystems IRIS instance from a backup restore point. You can restore the instance to its original location or to another server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the restore point from which you want to restore the InterSystems IRIS instance. | Accepts the Object object. To get this object, run the [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| ServerName | For the RestoreToAnotherLocation parameter set. Specifies the DNS name or IP address of the server to which you want to restore the InterSystems IRIS instance. | String | True | Named | False |
| ServerCredentials | For the RestoreToAnotherLocation parameter set. Specifies the credentials to authenticate against the target server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| PathMapping | Specifies an array of path mapping rules that redirect the InterSystems IRIS instance data to new target paths. If you do not specify this parameter, the cmdlet will restore the data to the original paths. | Accepts the [VBRIrisInstancePathMappingRule[]](vbririsinstancepathmappingrule.md) object. To create this object, run the [New-VBRIrisInstancePathMappingRule](new-vbririsinstancepathmappingrule.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will overwrite the data in non-empty target paths. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSession object that contains the InterSystems IRIS instance restore session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring an InterSystems IRIS Instance to the Original Location

|  |  |
| --- | --- |
| This example shows how to restore an InterSystems IRIS instance from a storage snapshot to its original location.  |  | | --- | | $rp = Get-VBRSnapshotRestorePoint -ObjectName "IRIS01"  Start-VBRIrisInstanceRestore -RestorePoint $rp[0] -Force |  Perform the following steps:   1. Run the [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) cmdlet. Specify the ObjectName parameter value. Save the result to the $rp variable. 2. Run the Start-VBRIrisInstanceRestore cmdlet. Set the $rp variable as the RestorePoint parameter value. Provide the Force parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring an InterSystems IRIS Instance to Another Server

|  |  |
| --- | --- |
| This example shows how to restore an InterSystems IRIS instance from a storage snapshot to another server and remap its data paths.  |  | | --- | | $rp = Get-VBRSnapshotRestorePoint -ObjectName "IRIS01"  $creds = Get-VBRCredentials -Name "iris\\administrator"  $rule = New-VBRIrisInstancePathMappingRule -OriginalPath "/usr/irissys/mgr" -TargetPath "/mnt/restore/mgr"  Start-VBRIrisInstanceRestore -RestorePoint $rp[0] -ServerName "172.18.21.30" -ServerCredentials $creds -PathMapping $rule -Force |  Perform the following steps:   1. Run the [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) cmdlet. Save the result to the $rp variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable. 3. Run the [New-VBRIrisInstancePathMappingRule](new-vbririsinstancepathmappingrule.md) cmdlet. Save the result to the $rule variable. 4. Run the Start-VBRIrisInstanceRestore cmdlet.  * Set the $rp variable as the RestorePoint parameter value. * Specify the ServerName parameter value. * Set the $creds variable as the ServerCredentials parameter value. * Set the $rule variable as the PathMapping parameter value. * Provide the Force parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring an InterSystems IRIS Instance from a NAS Backup to the Original Location

|  |  |
| --- | --- |
| This example shows how to restore an InterSystems IRIS instance from a NAS backup to its original location.  |  | | --- | | $rp = Get-VBRUnstructuredBackupRestorePoint  Start-VBRIrisInstanceRestore -RestorePoint $rp[0] |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $rp variable. 2. Run the Start-VBRIrisInstanceRestore cmdlet. Set the $rp variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring an InterSystems IRIS Instance from a NAS Backup to Another Server

|  |  |
| --- | --- |
| This example shows how to restore an InterSystems IRIS instance from a NAS backup to another server.  |  | | --- | | $rp = Get-VBRUnstructuredBackupRestorePoint  $creds = Add-VBRCredentials -Type "Linux" -User "root" -Password "Test123!"  Start-VBRIrisInstanceRestore -RestorePoint $rp[0] -ServerName "skorhel1" -ServerCredentials $creds |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $rp variable. 2. Run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. Specify the Type, User, and Password parameter values. Save the result to the $creds variable. 3. Run the Start-VBRIrisInstanceRestore cmdlet.  * Set the $rp variable as the RestorePoint parameter value. * Specify the ServerName parameter value. * Set the $creds variable as the ServerCredentials parameter value. |

Related Commands

* [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRIrisInstancePathMappingRule](new-vbririsinstancepathmappingrule.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)
* [Add-VBRCredentials](add-vbrcredentials.md)

Page updated 2026-06-18

