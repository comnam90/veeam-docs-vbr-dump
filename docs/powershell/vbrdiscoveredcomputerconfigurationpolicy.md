---
title: "VBRDiscoveredComputerConfigurationPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdiscoveredcomputerconfigurationpolicy.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRDiscoveredComputerConfigurationPolicy


Contains a configuration policy.

| Property | Type | Description |
| --- | --- | --- |
| AgentType | VBRAgentType | The type of a Veeam Agent:   * Windows * Linux * Mac * Unix |
| Scope | GUID | IDs of discovered computers or protection groups. |
| ConfigurationOption | VBRDiscoveredComputerConfigurationOption | Configuration option for Veeam Agent settings. |
| AppliedTo | GUID | IDs of computers to which the policy is assigned. |
| Id | GUID | ID of the policy. |


