---
title: "VBRDiscoveredMongoDBReplicaSetNode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdiscoveredmongodbreplicasetnode.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# VBRDiscoveredMongoDBReplicaSetNode


Contains discovered MongoDB replica set nodes.

Properties

| Property | Type | Description |
| --- | --- | --- |
| EntityType | [VBRDiscoveredMongoDBEntityType](enums.md#VBRDiscoveredMongoDBEntityType) | Discovered MongoDB entity type. |
| ReplicaSetId | GUID | Unique ID for the specific replica set. |
| HostId | GUID | Unique ID for the host. |
| HostName | String | Unique ID for the name of the host. |
| Port | Int32 | The port that Veeam Backup & Replication will use to route requests between the MongoDB database and backup infrastructure components. |
| IsHealthy | Boolean | Replica set node health status. |
| IsPrimary | Boolean | Replica set node set as a primary backup node. |
| IsHidden | Boolean | Hidden replica set node. |


