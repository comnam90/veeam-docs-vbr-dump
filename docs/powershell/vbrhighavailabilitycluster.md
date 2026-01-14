---
title: "VBRHighAvailabilityCluster"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrhighavailabilitycluster.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# VBRHighAvailabilityCluster

In this article

Contains information on the high availability cluster.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Primary | VBRHighAvailabilityClusterNode | Primary cluster node. |
| Secondary | VBRHighAvailabilityClusterNode[] String | Secondary cluster node. |
| ClusterEndpoint | String | IP address of the cluster, |
| ClusterDnsName | String | Cluster DNS name. |
| IsCreationInProgress | Boolean | Defines whether the high availability cluster creation is processing. |
| IsFailoverInProgress | Boolean | Defines whether failover is in progress. |
| IsRemovalInProgress | Boolean | Defines whether the high availability cluster disassemble is in progess. |
| IsAnyActivityInProgress | Boolean | Defines whether the following processes run on the high availability cluster:   * Cluster creation * Failover * Cluster disassemble |
| IsHealthyCluster | Boolean | Defines whether the high availability cluster state. |

Related Commands

* [Add-VBRHighAvailabilityCluster](add-vbrhighavailabilitycluster.md)
* [Get-VBRHighAvailabilityCluster](get-vbrhighavailabilitycluster.md)

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
