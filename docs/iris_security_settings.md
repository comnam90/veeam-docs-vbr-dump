---
title: "Configuring Security Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_security_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Security Settings


When you configure the backup infrastructure for InterSystems IRIS protection in Veeam Backup & Replication, you can specify the security settings that Veeam Backup & Replication uses to establish a secure connection between the backup server and protected ODB servers. By default, Veeam Backup & Replication offers the following security settings:

* To establish a secure connection between the backup server and ODB servers, Veeam Backup & Replication uses the default self-signed TLS certificate.
* Veeam Backup & Replication allows all Linux-based computers to connect to the backup server using the SSH fingerprint.

Keep in mind that the default security settings are intended for testing and evaluation purposes only. To prevent potential security issues in a production environment, change the security settings. For example, you can use a custom TLS certificate and enable verification of Linux host SSH fingerprints.

For details on other security settings available in Veeam Backup & Replication, see [Configuring Security Settings](vbr_settings_security.md).

In This Section

* [Managing TLS Certificates](iris_security_settings_tls_cert.md)
* [Adding Computers to Trusted Hosts List](iris_security_settings_ssh_trust.md)
* [Registering Storage System for Application Protection](iris_storage_registration.md)

Page updated 2026-07-28

