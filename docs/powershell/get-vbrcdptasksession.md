---
title: "Get-VBRCDPTaskSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdptasksession.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCDPTaskSession

In this article

Short Description

Returns VMs processed during CDP policy sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get VMs processed during specified CDP policy session.

|  |
| --- |
| Get-VBRCDPTaskSession -Session <VBRCDPSession> [-Last]  [<CommonParameters>] |

* Get VMs processed during specified CDP policy session by the session ID.

|  |
| --- |
| Get-VBRCDPTaskSession [-Id <guid>]  [<CommonParameters>] |

* Get the last VMs processed during a CDP policy session by VMs ID.

|  |
| --- |
| Get-VBRCDPTaskSession [-Last] [-ObjectId <guid>]  [<CommonParameters>] |

* Get the last VMs processed during a CDP policy session by VMs name.

|  |
| --- |
| Get-VBRCDPTaskSession [-Last] [-ObjectName <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns VMs performed during CDP policy sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a CDP policy session that processes VMs. The cmdlt will return these VMs. | Accepts the VBRCDPSession object. To create this object, run the [Get-VBRCDPSession](get-vbrcdpsession.md) cmdlet. | True | Named | True (ByPropertyName) |
| Last | Defines that the cmdlet will return the last VMs that were processed during a CDP policy session. | SwitchParameter | False | Named | False |
| Id | Specifies an ID of a session that you want to get. | Guid | False | Named | False |
| ObjectId | Specifies an ID of VMs that processed during a CDP policy session. | Guid | False | Named | False |
| ObjectName | Specifies a name of VMs that processed during a CDP policy session. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPTaskSession object that contains information on VMs performed during CDP policy sessions.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting VMs Processed During Specific CDP Policy Session

|  |  |
| --- | --- |
| This example shows how to get VMs processed during the CDP policy session.  |  | | --- | | $policy = Get-VBRCDPPolicy -Name "VM079"  $session = Get-VBRCDPSession -Policy $policy -Last  Get-VBRCDPTaskSession -Session $session |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable. 2. Run the [Get-VBRCDPSession](get-vbrcdpsession.md) cmdlet. Set the $policy variable as the Policy parameter value. Provide the Last parameter. Save the result to the $session variable. 3. Run the Get-VBRCDPTaskSession cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VMs Processed During CDP Policy Session by Session ID

|  |  |
| --- | --- |
| This command returns the VMs processed during the 402e082c-4a6d-4a9b-86c8-3330f35e9773 CDP policy session.  |  | | --- | | Get-VBRCDPTaskSession -Id "402e082c-4a6d-4a9b-86c8-3330f35e9773" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting VM Processed During CDP Policy Session by VMs ID

|  |  |
| --- | --- |
| This command returns the 15e56946-b75c-444a-9022-99f15ee0b9a2 VM processed during a CDP policy session.  |  | | --- | | Get-VBRCDPTaskSession -ObjectId "15e56946-b75c-444a-9022-99f15ee0b9a2" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Last VM Processed During CDP Policy Session

|  |  |
| --- | --- |
| This command returns the last VMs processed during a CDP policy session.  |  | | --- | | Get-VBRCDPTaskSession -Last | |

Related Commands

* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)
* [Get-VBRCDPSession](get-vbrcdpsession.md)

Page updated 6/12/2024

Page content applies to build 13.0.1.1071
