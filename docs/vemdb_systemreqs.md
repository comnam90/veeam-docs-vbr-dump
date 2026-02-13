---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_systemreqs.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# System Requirements


This section lists system requirements for Veeam Explorer for MongoDB.

| Component | Requirement |
| --- | --- |
| OS | Veeam Explorer for MongoDB supports MongoDB deployments running on the 64-bit versions of the following Linux distributions:  * Debian 11.0 - 12.5 * Ubuntu 20.04, 22.04 and 24.04 * RHEL 8.4 - 9.6 * Rocky Linux 8.10, 9.4 - 9.6 * AlmaLinux 8.10, 9.4 - 9.6 * SLES 12 SP5, 15 SP3 - 15 SP5 * Oracle Linux 7 - 9 (RHCK)   For details on the MongoDB platform support matrix, see [MongoDB Docs](https://www.mongodb.com/docs/manual/administration/production-notes/#platform-support-matrix). |
| MongoDB | Veeam Explorer for MongoDB supports the following solutions for MongoDB 7.0, 8.0:   * MongoDB Community Edition * MongoDB Enterprise Advanced * Percona Server for MongoDB   Depending on the protection group configuration, Veeam Backup & Replication connects to MongoDB using MongoDB Wire Protocol and one of the following methods:   * SCRAM * SCRAM with TLS * x509 certificate with TLS   For details, see [Authentication Against Replica Set](mongo_auth_methods.md).  Notes:   * Standalone servers with MongoDB deployments are not supported. * MongoDB sharded clusters are not supported. |


