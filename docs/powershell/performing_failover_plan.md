---
title: "Performing Failover by Failover Plan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/performing_failover_plan.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Performing Failover by Failover Plan


To perform failover by failover plan with Veeam PowerShell snap-in, you need to perform the following steps:

1. Create VM objects: run the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet to create an object for each VM that you want to add to the failover plan.

You can edit the created VM objects with the [Set-VBRFailoverPlanObject](set-vbrfailoverplanobject.md) cmdlet afterwards.

1. Create the failover plan: run the [Add-VBRFailoverPlan](add-vbrfailoverplan.md) cmdlet to create the failover plan. Use the created VM objects to add VM to your plan.

If you need to edit a created failover plan, run the [Set-VBRFailoverPlan](set-vbrfailoverplan.md) cmdlet.

1. Launch failover by the failover plan: run the [Start-VBRFailoverPlan](start-vbrfailoverplan.md) cmdlet to launch the failover process. Use the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet to look for the failover plan you need.

You can launch failover plan that were created with UI as well.

1. Finalize the failover process:

1. Undo failover is the only available option to finalize failover as a group. Undo failover switches workload back to the original VMs, revert replication operations and discard changes made to the working VM replicas. In this case you loose all the changes that were made to the replicas while you failed over to them. Run the [Undo-VBRFailoverPlan](undo-vbrfailoverplan.md) cmdlet to undo failover of the group.
2. Fail back if you want to switch back to the original VMs and keep the changes made to replicas. Run the [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) cmdlet. You need to process each VM individually.
3. Commit failover if you want to permanently move the workload to replica. Run the [Start-VBRViReplicaFailover](start-vbrvireplicafailover.md) cmdlet with Definite parameter. You need to process each VM individually.

This example demonstrates how to create a failover plan for a group of Microsoft Exchange servers and a DNS server, run and undo it.

|  |
| --- |
| // Create VM objects:  $DNS = Find-VBRViEntity -Name "DNSServer" | New-VBRFailoverPlanObject -BootDelay 0  $MSExchange01 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_01" | New-VBRFailoverPlanObject -BootOrder 1  -BootDelay 180  $MSExchange02 = Find-VBRViEntity -Name "MS\_Exchange\_Server\_02" | New-VBRFailoverPlanObject -BootOrder 2  -BootDelay 120    // Create failover plan:  Add-VBRFailoverPlan -Name "MS Exchange Group Failover" -FailoverPlanObject $DNS, $MSexchange01, $MSExchange02 -Description "Failover plan for the mail servers group: DNS Server, MS Exchange 01 Server, MS Exchange 02 Server"    // Launch failover plan:  Get-VBRFailoverPlan -Name "MS Exchange Group Failover" | Start-VBRFailoverPlan    // Undo failover:  Get-VBRFailoverPlan -Name "MS Exchange Group Failover" | Undo-VBRFailoverPlan |


