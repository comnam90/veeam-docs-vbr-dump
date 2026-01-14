---
title: "Application Group"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/application_group.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Application Group

In this article

In most cases, a machine works not alone but in cooperation with other services and components. To verify such machine, you first need to start all services and components on which this machine is dependent. To this aim, Veeam Backup & Replication uses the application group.

The application group creates the “surroundings” for the verified machine. The application group contains one or several machines on which the verified machine is dependent. These machines run applications and services that must be started to enable fully functional work of the verified machine. Typically, the application group contains at least a domain controller, DNS server and DHCP server.

When you set up an application group, you specify a role of every machine and its boot priority. Additionally, you can specify what tests must be performed to verify machines in the application group.

When a SureBackup job is launched, Veeam Backup & Replication first starts in the virtual lab machines from the application group in the required order and performs necessary tests against them. This way, Veeam Backup & Replication creates the necessary environment for the verified machine. Only after all machines from the application group are started and tested, Veeam Backup & Replication starts the verified machine in the virtual lab.

For example, if you want to verify a Microsoft Exchange Server, you need to test its functionality in cooperation with the domain controller and DNS server. Subsequently, you must add to the application group a virtualized domain controller and DNS server. When Veeam Backup & Replication runs a SureBackup job, it will first start and verify the domain controller and DNS server in the virtual lab to make verification of the Microsoft Exchange Server possible.

Related Topics

[Creating Application Groups](appgroup_create.md)

Page updated 4/29/2025

Page content applies to build 13.0.1.1071
