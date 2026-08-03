---
title: "/cloud"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloud.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud


Represents a collection of Veeam Cloud Connect resources.

The /cloud resource provides a set of links to the following Veeam Cloud Connect resources:

* [CloudGateway](cloudgateways.md)
* [CloudGatewayPool](cloudgatewaypools.md)
* [CloudTenant](tenants.md)
* [CloudHardwarePlan](hardwareplans.md)
* [CloudPublicIpAddress](publicipaddresses.md)
* [CloudFailoverPlan](cloudfailoverplans.md)
* [CloudVmReplicaPoint](cloudvmreplicapoints.md)
* [CloudReplica](cloudreplicas.md)
* [VlanConfiguration](vlans.md)
* [CloudFailoverSession](cloudfailoversessions.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud |

Related Resources

None.

Methods

The following methods are supported for the /cloud resource:

[GET /cloud](get_cloud.md)

Resource Representation

The /cloud resource has a resource representation of the following type:

|  |
| --- |
| <CloudConnectService Href="http://local.host:9399/api/cloud" Type="CloudConnectService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/logonSessions/b30eccda-7cc4-414e-b407-dab96abb6e1d" Type="LogonSession" Rel="Up"/>     <Link Href="http://local.host:9399/api/cloud/gateways" Type="CloudGatewayReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants" Type="CloudTenantReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/hardwarePlans" Type="CloudHardwarePlanReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/publicIpAddresses" Type="CloudPublicIpAddressReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/cloudFailoverPlans" Type="CloudFailoverPlanReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vmReplicaPoints" Type="CloudVmReplicaPointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/replicas" Type="CloudReplicaReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vlans" Type="VlanConfigurationReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/failoverSessions" Type="CloudFailoverSessionReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gatewayPools" Type="CloudGatewayPoolReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gateways?format=Entity" Type="CloudGatewayList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants?format=Entity" Type="CloudTenantList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/hardwarePlans?format=Entity" Type="CloudHardwarePlanList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/publicIpAddresses?format=Entity" Type="CloudPublicIpAddressList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/cloudFailoverPlans?format=Entity" Type="CloudFailoverPlanList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vmReplicaPoints?format=Entity" Type="CloudVmReplicaPointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/replicas?format=Entity" Type="CloudReplicaList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vlans?format=Entity" Type="VlanConfigurationList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/failoverSessions?format=Entity" Type="CloudFailoverSessionList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gatewayPools?format=Entity" Type="CloudGatewayPoolList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gateways" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/tenants" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/hardwarePlans" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/publicIpAddresses" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/gatewayPools" Rel="Create"/>   </Links> </CloudConnectService> |

Page updated 2026-07-29

