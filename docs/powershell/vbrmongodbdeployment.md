---
title: "VBRMongoDBDeployment"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmongodbdeployment.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# VBRMongoDBDeployment


Contains MongoDB replica sets or containers, also known as deployments.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | String | Unique MongoDB replica set or container ID. |
| Name | String | MongoDB replica set or container name. |
| HostName | String | Name of host where deployment resides. |
| Port | Int32 | The port that Veeam Backup & Replication will use to route requests between the MongoDB deployment and backup infrastructure components. |
| Credentials | CInternalCredentials | Credentials for a MongoDB replica set or container. |
| UseTls | Boolean | Use of TLS protocol to provide additional privacy and data integrity. |
| Type | [VBRMongoDBDeploymentType](enums.md#VBRMongoDBDeploymentType) | Type of MongoDB deployment. |


