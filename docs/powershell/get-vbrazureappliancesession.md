---
title: "Get-VBRAzureApplianceSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureappliancesession.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureApplianceSession


Short Description

Returns statuses of deployment sessions for helper restore appliance.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* For getting the statuses of all sessions.

|  |
| --- |
| Get-VBRAzureApplianceSession  [<CommonParameters>] |

* For getting the status of a specific session.

|  |
| --- |
| Get-VBRAzureApplianceSession [-Session <VBRAzureApplianceSession>]  [<CommonParameters>] |

* For getting the status of a specific session by the session ID.

|  |
| --- |
| Get-VBRAzureApplianceSession [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns status of process initiated by the [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the ID of the session. The cmdlet will return the statuses of the  sessions with this ID. | Guid | False | Named | True (ByProperty Name) |
| Session | Specifies the session. The cmdlet will return the status of this session. | Accepts the VBRAzureApplianceSession object. To get this object, run the [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureApplianceSession](vbrazureappliancesession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Statuses of All Sessions

|  |  |
| --- | --- |
| This command returns statuses of all sessions.  |  | | --- | | Get-VBRAzureApplianceSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Status of Specific Session

|  |  |
| --- | --- |
| This command returns status of a specific session. In this example, we assume that the user saved the session to a variable when they deployed the appliance. See examples for the [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) cmdlet for details.  |  | | --- | | Get-VBRAzureApplianceSession -Session $appliancesession | |


