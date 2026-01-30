---
title: "Get-VBRCDPSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdpsession.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCDPSession


Short Description

Returns CDP policy sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a session for the specified CDP policy.

|  |
| --- |
| Get-VBRCDPSession -Policy <VBRCDPPolicyBase> [-Last]  [<CommonParameters>] |

* Get a CDP policy session with a specific session ID.

|  |
| --- |
| Get-VBRCDPSession -Id <guid>  [<CommonParameters>] |

* Get a specified CDP policy session.

|  |
| --- |
| Get-VBRCDPSession -Session <VBRSession>  [<CommonParameters>] |

* Get a CDP policy session with the specified result.

|  |
| --- |
| Get-VBRCDPSession -Policy <VBRCDPPolicyBase> [-Result {None | Success | Warning | Failed}]  [<CommonParameters>] |

* Get a CDP policy session with the specified state.

|  |
| --- |
| Get-VBRCDPSession -Policy <VBRCDPPolicyBase> [-State {Stopped | Starting | Stopping | Working | Pausing | Resuming | WaitingTape | Idle | Postprocessing | WaitingRepository | Pending | WaitingSlot | ActionRequired}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns CDP policy sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies the CDP policy for which you want to get sessions. | Accepts the VBRCDPPolicyBase object. To create this object, run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. | True | Named | True (ByPropertyName) |
| Id | Specifies the ID of the session. The cmdlet will return the session with this ID. | Guid | True | Named | True (ByPropertyName) |
| Session | Specifies the CDP policy session for which you want to get an updated state. | Accepts the [VBRSession](vbrsession.md) object. To create this object, run the [Get-VBRSession](get-vbrsession.md) cmdlet. | False | Named | False |
| Last | Defines that the command returns the last session of the specified CDP policy. | SwitchParameter | False | Named | False |
| Result | Specifies the session result. The cmdlet will return sessions with the on of the following results:   * None * Success * Warning * Failed | VBRSessionResult | False | Named | False |
| State | Specifies the session state. The cmdlet will return sessions with the specified state. | [VBRSessionState](enums.md#vbrsessionstate) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPSession object that returns details on CDP policy sessions.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Session for Specified CDP Policy

|  |  |
| --- | --- |
| This example shows how to get the session for the VM079 CDP policy.  |  | | --- | | $policy = Get-VBRCDPPolicy -Name "VM079"  Get-VBRCDPSession -Policy $policy |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable. 2. Run the Get-VBRCDPSession cmdlet. Set the $policy variable as the Policy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting CDP Policy Session with Specific ID

|  |  |
| --- | --- |
| This command returns the 8a3eec9a-1ff0-4594-a454-522c410f76ab CDP policy session.  |  | | --- | | Get-VBRCDPSession -Id "8a3eec9a-1ff0-4594-a454-522c410f76ab" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting CDP Policy Session with Specific Result

|  |  |
| --- | --- |
| This example shows how to get a CDP policy session with the Failed result.  |  | | --- | | $policy = Get-VBRCDPPolicy -Name "VM079"  Get-VBRCDPSession -Policy $policy -Result Failed |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable.  1. Run the Get-VBRCDPSession cmdlet. Set the $policy variable as the Policy parameter value. Set the Failed option for the Result parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting CDP Policy Session with Specific State

|  |  |
| --- | --- |
| This example shows how get a CDP policy session with the Pending state.  |  | | --- | | $policy = Get-VBRCDPPolicy -Name "VM079"  Get-VBRCDPSession -Policy $policy -State Pending |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable.  1. Run the Get-VBRCDPSession cmdlet. Set the $policy variable as the Policy parameter value. Set the Pending option for the State parameter. |

Related Commands

* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)
* [Get-VBRSession](get-vbrsession.md)


