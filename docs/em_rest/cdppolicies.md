---
title: "/cdpPolicies"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdppolicies.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpPolicies


Represents a collection of all CDP policies created on all backup servers connected to Veeam Backup Enterprise Manager. The collection includes CDP policies for VMware vSphere and VMware Cloud Director.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpPolicies |

Related Resources

[/cdpPolicies/{ID}](cdppolicies_id.md)

Methods

The following methods are supported for the /cdpPolicies resource:

[GET /cdpPolicies](get_cdppolicies.md)

Resource Representation

The /cdpPolicies resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Ref UID="urn:veeam:CdpPolicy:8846d24b-d12f-4b7a-94e2-8c78241b841e" Name="CDP Policy Cloud Director" Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e" Type="CdpPolicyReference">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e?format=Entity" Name="CDP Policy Cloud Director" Type="CdpPolicy" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:CdpPolicy:9eeb2596-ec5c-42d5-98e6-7c1fe84fcc82" Name="CDP Policy DB Servers" Href="https://enterprise04.tech.local:9398/api/cdpPolicies/9eeb2596-ec5c-42d5-98e6-7c1fe84fcc82" Type="CdpPolicyReference">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/9eeb2596-ec5c-42d5-98e6-7c1fe84fcc82?format=Entity" Name="CDP Policy DB Servers" Type="CdpPolicy" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

