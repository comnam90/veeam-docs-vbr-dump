---
title: "understanding_veeam_explorers_cmdlets"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/understanding_veeam_explorers_cmdlets.html"
last_updated: "3/21/2025"
product_version: "13.0.1.1071"
---


In this article

A cmdlet is a specialized .NET class that interacts with Microsoft .NET Framework objects. Each cmdlet acts as a single-function command that can perform multiple operations with these objects. Objects represent instances of the Veeam backup infrastructure: jobs, databases, restore sessions and so on.

Each cmdlet has parameters that pass additional object data to cmdlet. Parameters can be either required or optional. You will not be able to run a cmdlet without specifying the required parameters, while the optional parameters can be omitted. Parameters are organized into parameter sets that form a syntax of the cmdlet.

|  |
| --- |
| Important |
| Veeam Explorers PowerShell does not support the use of square brackets in cmdlet syntax. |

Cmdlets and their parameters are named after the Windows PowerShell naming conventions. Veeam cmdlets are developed to behave like other Microsoft Windows cmdlets.

This guide covers only basic information on how to work with Veeam Explorers cmdlets using Windows PowerShell. For more information about Windows PowerShell, see this [Microsoft article](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.5).

Input and Output

As an input, the cmdlets expect objects, and they output objects. The objects mostly represent instances of the backup infrastructure: backups, jobs, job settings, switchover settings and so on. The objects can be part of a pipeline.

You can use the cmdlet help to understand what kind of input is needed. The cmdlets have syntax that shows the whole set of parameters available in the cmdlet and what each parameter expects as input.

For example, the [Start-VBOSharePointItemRestoreSession](start-vbosharepointitemrestoresession.md) cmdlet has the following syntax:

|  |
| --- |
| Start-VBOSharePointItemRestoreSession [-Job] <IVBOJob> [-Server <String>] [-Credential <PSCredential>][-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>]  Start-VBOSharePointItemRestoreSession [-Organization] <IVBOOrganization> [-Server <String>][-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>][<CommonParameters>]  Start-VBOSharePointItemRestoreSession [[-Job] <IVBOJob>] [[-Organization] <IVBOOrganization>] [-RestorePoint] <IVBORestorePoint> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>][-ShowDeleted] [-ShowAllVersions] [-Reason <String>][<CommonParameters>]  Start-VBOSharePointItemRestoreSession [[-Job] <IVBOJob>] [[-Organization] <IVBOOrganization>][-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions][-LatestState] [-Reason <String>] [<CommonParameters>] |

The [Start-VBOSharePointItemRestoreSession](start-vbosharepointitemrestoresession.md) cmdlet has four parameter sets for different types of restore:

* Restore from backups created by a specific Veeam Backup for Microsoft 365 job
* Restore from backups created for a specific organization
* Restore from a specific restore point
* Restore from the latest restore point

To restore SharePoint items backed up with Veeam Backup for Microsoft 365, you must provide at least one of the following required parameters:

| Parameter | Description |
| --- | --- |
| Job | Specifies a backup job to start a new restore session. You will be able to use the session to perform operations with items backed up by this job.  Accepts the IVBOJob object. To get this object, run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with items that this restore point contains.  Accepts the IVBORestorePoint object. To get this object, run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. |
| LatestState | Defines that the cmdlet will retrieve items from the latest restore point. If you provide this parameter, you will be able to perform operations with items in the most recent restore state. |

You can also use the following optional parameters to specify restore settings:

| Parameter | Description |
| --- | --- |
| Server | Specifies DNS name or IP address of the Veeam Backup for Microsoft 365 server that backed up items you want to restore. |
| Organization | Specifies an organization to start a new restore session. You will be able to use the session to perform operations with items backed up for this organization.  Accepts the IVBOOrganization object. To get this object, run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. |
| Credential | Specifies credentials that will be used for authenticating to the Veeam Backup for Microsoft 365 server. |
| Port | Specifies a port number that will be used to connect to the Veeam Backup for Microsoft 365 server. |
| ShowDeleted | Defines that deleted items will be included in the current session.  If you provide this parameter, you will be able to perform operations with these items. |
| ShowAllVersions | Defines that all versions of SharePoint items will be included in the current session.  If you provide this parameter, you will be able to perform operations with these items. Otherwise, only the latest version of SharePoint items will be available. |
| Reason | Specifies a reason to perform restore operation. |

The cmdlet returns the [VBOSharePointRestoreSession](vbosharepointrestoresession.md) object that contains settings of the restore session started to perform operations with backed-up SharePoint items.

Querying Objects

In Get cmdlets, some parameters support wildcard characters with which you can query objects returned by the cmdlet. This allows you to filter results by defined criteria.

For example, you can use the wildcard characters \* and ? when specifying values for the Name and DisplayName parameters:

* ABC\* — returns all objects with a name or display name that starts with ABC.
* ?ABC — returns all objects with a name or display name where a single character precedes ABC.

For the complete list of supported query parameters in Veeam Backup for Microsoft 365, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide.

Page updated 3/21/2025

Page content applies to build 13.0.1.1071
