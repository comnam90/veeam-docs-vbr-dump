---
title: "/cloud/cloudFailoverPlans/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoverplans_id_includes.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/cloudFailoverPlans/{ID}/includes


Represents a collection of VMs added to the cloud failover plan.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}/includes |

Related Resources

* [/cloud/cloudFailoverPlans/{ID}](cloudfailoverplans_id.md)
* [/cloud/cloudFailoverPlans/{ID}/includes/{ID}](cloudfailoverplans_id_includes_id.md)

Methods

The following methods are supported for the /cloud/cloudFailoverPlans/{ID}/includes resource:

[GET /cloud/cloudFailoverPlans/{ID}/includes](get_cloudfailoverplans_id_includes.md)

Resource Representation

The /cloud/cloudFailoverPlans/{ID}/includes resource has a resource representation of the following type:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <CloudFailoveredVms xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <CloudFailoveredVm Href="https://enterprise06.tech.local:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes/592cd62d-c7a2-4f19-a545-ed73ab696e42" Type="CloudFailoveredVm">         <FailoverPlanVMId>592cd62d-c7a2-4f19-a545-ed73ab696e42</FailoverPlanVMId>         <Name>apache05</Name>         <Order>0</Order>     </CloudFailoveredVm>     <CloudFailoveredVm Href="https://enterprise06.tech.local:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes/6fac81de-6012-45ff-adba-e01d28b19914" Type="CloudFailoveredVm">         <FailoverPlanVMId>6fac81de-6012-45ff-adba-e01d28b19914</FailoverPlanVMId>         <Name>enterprise04</Name>         <Order>1</Order>     </CloudFailoveredVm> </CloudFailoveredVms> |

Page updated 2026-07-29

