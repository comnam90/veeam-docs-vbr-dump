---
title: "VBRMongoDBCustomCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmongodbcustomcredentials.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# VBRMongoDBCustomCredentials

In this article

Contains custom credentials for individual computers within MongoDB containers or replica sets.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Computer | [VBRMongoDBComputer](vbrmongodbcomputer.md) | Individual computer within a MongoDB container or replica set. |
| Credentials | CCredentials | Credentials for an individual computer within a MongoDB container or replica set. |
| Endpoint | String | Endpoint for computer operations within a MongoDB container or replica set. |
| UseTemporaryCertificate | Boolean | Temporary certificate to use instead of credentials for an individual computer within a MongoDB container or replica set. |
| UseTemporarySshCredentials | Boolean | Single-use credentials to access Linux machines. |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
