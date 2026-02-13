---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_plan_and_manage_requirements.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Make sure that components in the plug-in management infrastructure meet the system requirements listed in this section.

Veeam Backup Server

For details on system requirements for the Veeam backup server and other Veeam Backup & Replication components, see [System Requirements](system_requirements.md) for Veeam Backup & Replication.

Computer with MongoDB

A computer with databases you want to protect using MongoDB Backup must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| OS | MongoDB Backup supports MongoDB deployments running on the 64-bit versions of the following distributions:  * Debian 11.0 - 12.5 * Ubuntu 20.04, 22.04 and 24.04 * RHEL 8.4 - 9.6 * Rocky Linux 8.10, 9.4 - 9.6 * AlmaLinux 8.10, 9.4 - 9.6 * SLES 12 SP5, 15 SP3 - 15 SP5 * Oracle Linux 7 - 9 (RHCK)   For details on the MongoDB platform support matrix, see [MongoDB Docs](https://www.mongodb.com/docs/manual/administration/production-notes/#platform-support-matrix). |
| MongoDB | MongoDB Backup supports the following solutions for MongoDB 7.0, 8.0:   * MongoDB Community Edition * MongoDB Enterprise Advanced * Percona Server for MongoDB   Depending on the protection group configuration, Veeam Backup & Replication connects to MongoDB using MongoDB Wire Protocol and one of the following methods:   * SCRAM * SCRAM with TLS * x509 certificate with TLS   For details, see [Authentication Against Replica Set](mongo_auth_methods.md).  Notes:   * Standalone servers with MongoDB deployments are not supported. * MongoDB sharded clusters are not supported. |

Network

Consider the following:

* A computer with MongoDB must be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, a computer with MongoDB cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway.
* Domain names of the computer with MongoDB deployment, Veeam Backup & Replication server and other servers in the Veeam backup infrastructure must be resolvable into IPv4 or IPv6 addresses.


