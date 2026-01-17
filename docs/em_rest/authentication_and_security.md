---
title: "Authentication and Security"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/authentication_and_security.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

When starting work with Veeam Backup Enterprise Manager REST API, the clients must first authenticate themselves. Client authentication involves two steps:

1. The client must log on to Veeam Backup Enterprise Manager with the user name and password. Veeam Backup Enterprise Manager REST API implements Basic HTTP Authentication as [defined by RFC 2617](http://www.ietf.org/rfc/rfc2617.txt).
2. The client must obtain an authorization token that must be used in all requests during the current logon session.

Similar to user authentication in the Veeam Backup Enterprise Manager Web UI, client authentication in the REST API dictates what operations the client is allowed to perform when working with the REST API. That is, if the client is authenticated using an account that does not have enough permissions to perform some actions, it will not be able to execute them. For example, if the client logs in using an account with the Restore Operator role (the role that only allows restoring files in Veeam Backup Enterprise Manager), the client will not be able to start, stop or edit a job. When the client sends a request to start a job, it will get the Access denied error with the 403 Forbidden status code.

In This Section

* [HTTP Authentication](http_authentication.md)
* [TLS Certificate](ssl_encryption.md)

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
