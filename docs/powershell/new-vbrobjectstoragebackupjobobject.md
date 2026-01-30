---
title: "New-VBRObjectStorageBackupJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrobjectstoragebackupjobobject.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRObjectStorageBackupJobObject


Short Description

Defines a scope of objects that will be added to the object storage backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRObjectStorageBackupJobObject -Server <VBRObjectStorageServer> [-Container <string>] [-Path <string>] [-IsObject] [-InclusionMask <VBRObjectStorageBackupMask[]>] [-ExclusionMask <VBRObjectStorageBackupMask[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRObjectStorageBackupJobObject object. This object contains a scope of objects that will be added to the object storage backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies object storage which data you want to back up. | Accepts the VBRObjectStorageServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Container | Specifies a bucket or a container that you want to back up. | String | False | Named | False |
| Path | Specifies object path or prefixes within a bucket or a container. | String | False | Named | False |
| IsObject | Note: This parameter is required if the path that you specify is an object.  Defines that the cmdlet will recognize the path as an object. If you omit this parameter, the cmdlet will recognize the path as the prefix. | SwitchParameter | False | Named | False |
| InclusionMask | Specifies a file mask for objects that you want to add to the object storage backup job. The cmdlet will back up only objects specified in this file mask. | Accepts the VBRObjectStorageBackupMask[] object. To get this object, run the [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md) cmdlet. | False | Named | False |
| ExclusionMask | Specifies a file mask for objects that you do not want to add to the object storage backup job. The cmdlet will not back up these objects. | Accepts the VBRObjectStorageBackupMask[] object. To get this object, run the following cmdles:   * [New-VBRObjectStorageBackupContainerPathMask](new-vbrobjectstoragebackupcontainerpathmask.md) * [New-VBRObjectStorageBackupServerPathMask](new-vbrobjectstoragebackupserverpathmask.md) * [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md) (for include and exclude) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupJobObject object that contains a scope of objects that will be added to the object storage backup job.

Examples

Defining Scope of Objects to Back up with Object Storage Backup Job

This example shows how to define a scope of objects that will be added to the object storage backup job. The cmdlet will add objects from the Montly backup container that are located within the Reports folder.

|  |
| --- |
| $serv = Get-VBRUnstructuredServer -Name "Azure OS"  $object = New-VBRObjectStorageBackupJobObject -Server $serv -Container "Monthly Backups" -Path "Reports" |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $serv variable.
2. Run the New-VBRObjectStorageBackupJobObject cmdlet. Set the $serv variable as the Server parameter value. Specify the Container parameter value. Specify the Path parameter value. Save the result to the $object variable.

Related Commands

* [Get-VBRUnstructuredServer](new-vbroracleprocessingoptions.md)
* [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md)


