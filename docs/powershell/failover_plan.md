---
title: "Veeam Cloud Connect Failover Plans"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/failover_plan.html"
last_updated: "9/4/2023"
product_version: "13.0.1.1071"
---

# Veeam Cloud Connect Failover Plans

In this article

You can use the cmdlets from this section to leverage cloud failover capabilities.

To fail over to your cloud replicas, you need to create a failover plan. For details, see [Failover Plans](fplan_cmdlets.md). For cloud failover plans, you need to use cloud-specific objects described in this section.

| Cmdlet | Operation |
| --- | --- |
| [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md) | Defines VM replicas failover plan |
| [Set-VBRCloudFailoverPlanObject](set-vbrcloudfailoverplanobject.md) | Modifies object with replicas added to the failover plan |
| [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) | Returns configuration of default gateways |
| [Set-VBRDefaultGatewayConfiguration](set-vbrdefaultgatewayconfiguration.md) | Modifies the configuration of default gateways |
| [Set-VBRDefaultGateway](set-vbrdefaultgateway.md) | Modifies the default gateway |
| [Remove-VBRDefaultGateway](remove-vbrdefaultgateway.md) | Removes the default gateway |
| [New-VBRFailoverPlanPublicIPRule](new-vbrfailoverplanpubliciprule.md) | Creates public IP mapping rule |

Page updated 9/4/2023

Page content applies to build 13.0.1.1071
