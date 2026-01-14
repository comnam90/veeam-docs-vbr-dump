---
title: "Configuring Security Settings for Veeam Plug-Ins"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/security_settings.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Configuring Security Settings for Veeam Plug-Ins

In this article

When you configure the backup infrastructure for enterprise applications in Veeam Backup & Replication, you can specify what security settings Veeam Backup & Replication will use to establish a secure connection between the backup server and protected computers. By default, Veeam Backup & Replication offers the following security settings:

* To establish a secure connection between parties, Veeam Backup & Replication uses the default self-signed TLS certificate.
* Veeam Backup & Replication allows all computers that run a Linux OS to establish a connection to the backup server using the SSH fingerprint.

Keep in mind that default security settings are only for testing and evaluation purposes. To prevent potential security issues, you can change security settings. For example, you can use a custom TLS certificate and verification of Linux host SSH fingerprints.

For details on other security settings, see [Configuring Security Settings](vbr_settings_security.md).

Related Topics

* [Managing TLS Certificates](security_settings_tls_cert.md)
* [Adding Computers to Trusted Hosts List](security_settings_ssh_trust.md)

Page updated 11/7/2025

Page content applies to build 13.0.1.1071
