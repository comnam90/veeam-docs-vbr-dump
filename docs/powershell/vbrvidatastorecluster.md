---
title: "VBRViDatastoreCluster"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvidatastorecluster.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# VBRViDatastoreCluster


Contains datastore cluster.

Properties

| Property | Type | Description |
| --- | --- | --- |
| ConnHost | CHost | The host to which the cluster is connected. |
| Type | VBRViType | The datastore cluster type. |
| Reference | string | The VMware identifier of the datastore cluster. |
| Capacity | int64 | The datastore cluster capacity. |
| FreeSpace | int64 | The free space on the datastore cluster. |
| Id | string | The datastore cluster ID. |
| Path | string | The datastore cluster infrastructure path. |
| Name | string | The datastore cluster name. |

Related Commands

[Find-VBRViDatastoreCluster](find-vbrvidatastorecluster.md)


