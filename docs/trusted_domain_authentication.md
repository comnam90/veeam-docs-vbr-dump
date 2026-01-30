---
title: "Trusted Domain Authentication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/trusted_domain_authentication.html"
last_updated: "12/11/2025"
product_version: "13.0.1.1071"
---

# Trusted Domain Authentication


Veeam Backup & Replication supports authentication for user accounts from trusted domains and forests. To use this feature, you must configure an Active Directory trust relationship. This enables administrators and users from external domains to access the Veeam Backup & Replication console without creating separate local accounts. For more information, see [this Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity/domain-services/concepts-forest-trust).

Before you use trusted domain authentication, consider the following:

* Veeam Backup & Replication on Linux does not support trusted domain authentication.
* You must establish a valid Active Directory trust relationship between the domain to which Veeam Backup & Replication belongs and the domain from which users will connect. Veeam Backup & Replication supports intra-forest and cross-forest trust types. You can configure trust relationships as one-way or two-way.

* Name resolution must function in both directions in two-way relationships.

* The Veeam Backup & Replication console uses Microsoft Windows authentication (Kerberos/NTLM). Proper DNS resolution must be possible between the domains and the client and server must use the established trust relationship. For more information, see [Kerberos Authentication](kerberos_authentication.md).

* When using one-way relationships, authentication is possible if the trust direction allows the Veeam Backup & Replication backup server domain to validate credentials from the trusted domain.
* When you log in to the Veeam Backup & Replication console using trusted domain authentication, you can use the Remember Me check box only if there is a two-way relationship between the domains.
* For authentication with Active Directory user accounts, the accounts must have the User logon name attribute populated in the Active Directory Users and Computers MMC snap-in.


