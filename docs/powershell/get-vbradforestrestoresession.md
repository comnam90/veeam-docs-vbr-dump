---
title: "Get-VBRADForestRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradforestrestoresession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRADForestRestoreSession


Short Description

Returns Microsoft Active Directory forest restore sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all active Microsoft Active Directory forest restore sessions.

|  |
| --- |
| Get-VBRADForestRestoreSession  [<CommonParameters>] |

* Get a specific Microsoft Active Directory forest restore session by session object.

|  |
| --- |
| Get-VBRADForestRestoreSession [-Session <VBRADForestRestoreSession>]  [<CommonParameters>] |

* Get a Microsoft Active Directory forest restore session by ID.

|  |
| --- |
| Get-VBRADForestRestoreSession [-Id <Guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft Active Directory forest restore sessions. You can get all active sessions, or filter by session object or session ID. Use this cmdlet to monitor or stop ongoing Microsoft Active Directory forest restore operations.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Session | Specifies a Microsoft Active Directory forest restore session. The cmdlet will return this session. | Accepts the [VBRADForestRestoreSession](vbradforestrestoresession.md) object. To get this object, run the Get-VBRADForestRestoreSession cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| Id | Specifies the ID of the Microsoft Active Directory forest restore session. The cmdlet will return this session. | Guid | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestRestoreSession](vbradforestrestoresession.md) object that contains properties of the Microsoft Active Directory forest restore session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active AD Forest Restore Sessions

|  |  |
| --- | --- |
| This command returns all active Microsoft Active Directory forest restore sessions.  |  | | --- | | Get-VBRADForestRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting AD Forest Restore Session by Session Object

|  |  |
| --- | --- |
| This example shows how to get a specific Microsoft Active Directory forest restore session using the session object.  |  | | --- | | $sessions = Get-VBRADForestRestoreSession  Get-VBRADForestRestoreSession -Session $sessions[0] |  Perform the following steps:   1. Run the Get-VBRADForestRestoreSession cmdlet. Save the result to the $sessions variable. The cmdlet returns an array of sessions. Note the ordinal number of the necessary session (in this example, it is the first session in the array). 2. Run the Get-VBRADForestRestoreSession cmdlet. Set the $sessions[0] variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting AD Forest Restore Session by ID

|  |  |
| --- | --- |
| This command returns the Microsoft Active Directory forest restore session with the specified ID.  |  | | --- | | Get-VBRADForestRestoreSession -Id "a1b2c3d4-e5f6-7890-abcd-ef1234567890" | |

Related Commands

[Start-VBRADForestRestore](start-vbradforestrestore.md)

Page updated 2026-07-28

