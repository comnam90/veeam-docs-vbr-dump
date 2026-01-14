---
title: "cloudfailoverplans_id_includes_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoverplans_id_includes_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM with the specified ID that is added to the cloud failover plan with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}/includes/{ID} |

Related Resources

* [/cloud/cloudFailoverPlans/{ID}](cloudfailoverplans_id.md)

* [/cloud/cloudFailoverPlans/{ID}/includes](cloudfailoverplans_id_includes.md)

Methods

The following methods are supported for the /cloud/cloudFailoverPlans/{ID}/includes/{ID} resource:

[GET /cloud/cloudFailoverPlans/{ID}/includes/{ID}](get_cloudfailoverplans_id_includes_id.md)

Resource Representation

The /cloud/cloudFailoverPlans/{ID}/includes/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <CloudFailoveredVm xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes/592cd62d-c7a2-4f19-a545-ed73ab696e42" Type="CloudFailoveredVm" xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
