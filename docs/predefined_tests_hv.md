---
title: "Predefined Tests"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/predefined_tests_hv.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Predefined Tests

In this article

Veeam Backup & Replication can verify machines with the following predefined tests:

* Heartbeat test. When the machine starts, Veeam Backup & Replication performs a heartbeat test. It waits for a heartbeat signal from Hyper-V Integration Services installed inside the machine to determine that the machine guest OS is running. If the signal comes regularly at specific time intervals, the test is passed.
* Ping test. Veeam Backup & Replication sends ping requests to the machine from the backup server and checks if the machine can respond to them. If the machine responds to ping requests, the test is passed.

Veeam Backup & Replication uses two algorithms for detecting the IP addresses of a Hyper-V machine:

+ Veeam Backup & Replication communicates with Hyper-V Integration Services installed inside the machine guest OS to detect the machine IP address.
+ Veeam Backup & Replication uses a special module in the proxy appliance to check the IP addresses of the machine started in the isolated network. This algorithm is used, for example, if the machine does not have Hyper-V Integration Services installed.

* Application test. Veeam Backup & Replication waits for applications inside the machine to start and runs a script against these applications. For DNS servers, domain controllers, Global Catalog servers, mail servers and web servers, Veeam Backup & Replication uses a script that probes an application-specific port. For example, to verify a domain controller, Veeam Backup & Replication probes port 389 for a response. If the response is received, the test is passed.
* [For Veeam Backup & Replication on Windows] Application test. Veeam Backup & Replication waits for applications inside the machine to start and runs a script against these applications. Veeam Backup & Replication uses two types of predefined scripts:

+ For DNS servers, domain controllers, Global Catalog servers, mail servers and web servers, Veeam Backup & Replication uses a script that probes an application-specific port. For example, to verify a domain controller, Veeam Backup & Replication probes port 389 for a response. If the response is received, the test is passed.
+ For Microsoft SQL Server, Veeam Backup & Replication uses a script that attempts to connect to instances and databases on the Microsoft SQL Server. For more information, see [Microsoft SQL Server Checker Script](custom_verification_scripts.md#sql).

|  |
| --- |
| Note |
| To run the heartbeat test, you must have Hyper-V Integration Services installed inside the machine. If Hyper-V Integration Services are not installed, this test will be skipped. |

You can run verification tests for machines added to the application group or processed with a linked SureBackup job. Settings for verification tests can be specified and customized in the application group or SureBackup job settings.

![Predefined Tests](images/surebackup_job_tests.webp)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
