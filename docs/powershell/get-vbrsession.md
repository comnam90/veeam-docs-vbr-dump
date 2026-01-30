---
title: "Get-VBRSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsession.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSession


Short Description

Returns jobs sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get the session for the specified job.

|  |
| --- |
| Get-VBRSession -Job <VBRJob> [-Last]  [<CommonParameters>] |

* Get the session with the specified ID.

|  |
| --- |
| Get-VBRSession -Id <guid[]>  [<CommonParameters>] |

* Get the specified session.

|  |
| --- |
| Get-VBRSession -Session <VBRSession>  [<CommonParameters>] |

* Get the session for the job with the specified result.

|  |
| --- |
| Get-VBRSession -Job <VBRJob> [-Result <VBRSessionResult> {None | Success | Warning | Failed}]  [<CommonParameters>] |

* Get the session for the job with the specified state.

|  |
| --- |
| Get-VBRSession -Job <VBRJob> [-State <VBRSessionState> {Stopped | Starting | Stopping | Working | Pausing |Resuming | WaitingTape | Idle | Postprocessing | WaitingRepository | Pending}]  [<CommonParameters>] |

* Get the session for the job of the specified type.

|  |
| --- |
| Get-VBRSession -Type <EDbJobType>  [<CommonParameters>] |

Detailed Description

This cmdlet returns sessions for a selected job.

|  |
| --- |
| Important |
| To get tape backup job sessions, tun the [Get-VBRTapeBackupSession](get-vbrtapebackupsession.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job for which you want to get sessions that have been run.  Note: This parameter does not accept VM copy and file copy job objects. | Accepts the [VBRJob](vbrjob.md) object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name) |
| Type | Specifies the type of the session. The cmdlet will return the session of this type. | EDbJobType | True | Named | True (ByPropertyName) |
| ID | Specifies the ID of the session. The cmdlet will return the session with this ID. | Guid[] | False | Named | False |
| Last | Defines that the command returns the last session of the specified job. | SwitchParameter | False | Named | False |
| Session | Specifies the job session for which you want to get an updated state. | Accepts the [VBRSession](vbrsession.md) object. To get this object, run the Get-VBRSession cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| State | Specifies the session state. The cmdlet will return sessions with the specified state. | [VBRSessionState](enums.md#vbrsessionstate) | False | Named | False |
| Result | Specifies the session result. The cmdlet will return sessions with the specified result:   * None * Success * Warning * Failed | VBRSessionResult | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Sessions for Specific Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the session for the specified job.  |  | | --- | | $job = Get-VBRJob -Name "Backup Copy Job"  $session = Get-VBRSession -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet to get the backup job. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Get-VBRSession cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Sessions for VM Copy and File Copy Type of Jobs

|  |  |
| --- | --- |
| This command shows how to get the sessions for the specified type of jobs.  |  | | --- | | Get-VBRSession -Type Copy | |

Related Commands

[Get-VBRJob](get-vbrjob.md)


