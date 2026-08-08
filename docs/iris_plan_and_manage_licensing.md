---
title: "Licensing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_plan_and_manage_licensing.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Licensing


To use Veeam Backup & Replication to protect InterSystems IRIS instances, you must have a valid Veeam Backup & Replication license. Licenses are installed and managed on the Veeam Backup & Replication server. If the license is not valid or out of resources, application backup policies fail.

This guide provides information only on the specifics of Veeam licenses for Epic EHR System Protection. For terminology and general information about Veeam licensing, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

Licensed Objects

Veeam Backup & Replication protects InterSystems IRIS instances using the same licensing model as other application backup policies. The unstructured data backup engine is used only as a tool to retrieve data and does not affect licensing.

If you use an instance-based ([Veeam Universal Licensing](https://www.veeam.com/universal-licensing.html)) license, each protected ODB server consumes one instance unit from the license. An ODB server is considered protected if it was processed by an application backup policy in the last 31 days.

A server protected at both the application level and the image level consumes a license only once. For example, if you back up the InterSystems IRIS instances on an ODB server with an application backup policy and also create image-level backups of the same server, only one license per server is consumed.

Supported License Types

You can use Epic EHR System Protection with the Veeam Universal License with all license packages (Veeam Backup Essentials, Veeam Backup & Replication, Veeam Availability Suite). If you use the Rental license type, Epic EHR System Protection is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

Obtaining and Managing Licenses

For details on how to install a license and monitor licensed objects, see [Licensing](licensing.md) for Veeam Backup & Replication.

Page updated 2026-08-06

