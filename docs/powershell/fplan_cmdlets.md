---
title: "Failover Plans"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/fplan_cmdlets.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Failover Plans

In this article

Failover plan is a preset scenario for one-click failover of a group of interdependent VMs. Failover plan is created by the user in advance and then used to perform failover of the group in case the primary VMs are out of service for any reason.

|  |
| --- |
| ![Failover Plans](images/icon_note.webp) Note: |
| Operations with failover plans require Enterprise or Enterprise Plus, Veeam Universal License product edition. |

In This Section

| Cmdlet | Operation |
| --- | --- |
| [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) | Creates an object containing the VM to add to the failover plan. |
| [Set-VBRFailoverPlanObject](set-vbrfailoverplanobject.md) | Modifies the object containing the VM to add to the failover plan. |
| [Add-VBRFailoverPlan](add-vbrfailoverplan.md) | Creates a failover plan. |
| [Get-VBRFailoverPlan](get-vbrfailoverplan.md) | Looks for existing failover plans. |
| [Set-VBRFailoverPlan](set-vbrfailoverplan.md) | Modifies the failover plan. |
| [Remove-VBRFailoverPlan](remove-vbrfailoverplan.md) | Removes the failover plan. |
| [Start-VBRFailoverPlan](start-vbrfailoverplan.md) | Starts failing the VMs over by failover plan. |
| [Undo-VBRFailoverPlan](undo-vbrfailoverplan.md) | Undoes failover by failover plan. |

Page updated 6/27/2024

Page content applies to build 13.0.1.1071
