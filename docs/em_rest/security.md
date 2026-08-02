---
title: "/security"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /security


Represents a security resource. The security resource provides access to Veeam Backup Enterprise Manager security settings and allows the client to manage roles used in Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security |

Related Resources

* [/security/roles](security_roles.md)
* [/security/accounts](security_accounts.md)

Methods

The following methods are supported for the /security resource:

[GET /security](get_security.md)

Resource Representation

The /security resource has a resource representation of the following type:

|  |
| --- |
| <EnterpriseSecuritySettings Href="http://local.host:9399/api/security" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/security/accounts" Type="EnterpriseAccountReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/security/roles" Type="EnterpriseRoleReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/security/accounts" Rel="Create"/>     <Link Href="http://local.host:9399/api/security/accounts?action=rebuildScope" Rel="Start"/>   </Links> </EnterpriseSecuritySettings> |

Page updated 2026-07-29

