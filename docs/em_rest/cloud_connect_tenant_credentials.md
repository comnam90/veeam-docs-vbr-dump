---
title: "Tenant Logon Session"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloud_connect_tenant_credentials.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Tenant Logon Session


Service providers can allow tenants to log on to Veeam Backup Enterprise Manager REST API and perform operations with resources available to a specific tenant. To create a new logon session for the tenant, you need to provide tenant credentials in the body of the POST HTTP request to the /sessionMngr/ resource.

The client can create logon sessions for the tenants of the following types:

* [Standalone tenant](#StandaloneCloudTenantLogon)
* [vCloud tenant](#vCloudTenantLogon)

For details on creating a new logon session, see [Perform Logon](logging_on.md).

Standalone Cloud Tenant Logon Session Creation

Credentials for the standalone tenant account must be provided in the TenantCredentials element.

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Username | String | User name of the tenant account. | Yes | 1/1 |
| Password | String | Password for the tenant account. | Yes | 1/1 |

For example:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

In the response, Veeam Backup Enterprise Manager will return a representation of the /sessionMngr/ resource with a link to the Cloud Connect service resource. For example:

|  |
| --- |
| <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/362da803-804d-4c32-ad35-0972e432460b">   <Links>     <Link Rel="Up" Type="EnterpriseManager" Href="https://localhost:9398/api/" />     <Link Rel="Down" Type="CloudConnectService" Href="https://localhost:9398/api/cloud" />     <Link Rel="Delete" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/362da803-804d-4c32-ad35-0972e432460b" />   </Links>   <UserName>SRV36\Administrator</UserName>   <SessionId>362da803-804d-4c32-ad35-0972e432460b</SessionId> </LogonSession> |

In the Cloud Connect service resource representation, Veeam Backup Enterprise Manager will return a list of resources with which the specified tenant can work using Veeam Backup Enterprise Manager REST API. For example:

|  |
| --- |
| <CloudConnectService xmlns="http://www.veeam.com/ent/v1.0" Type="CloudConnectService" Href="https://localhost:9398/api/cloud">   <Links>     <Link Rel="Up" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/362da803-804d-4c32-ad35-0972e432460b" />     <Link Rel="Down" Type="CloudFailoverPlanReferenceList" Href="https://localhost:9398/api/cloud/cloudFailoverPlans" />     <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints" />     <Link Rel="Down" Type="CloudReplicaReferenceList" Href="https://localhost:9398/api/cloud/replicas" />     <Link Rel="Down" Type="CloudFailoverPlanList" Href="https://localhost:9398/api/cloud/cloudFailoverPlans?format=Entity" />     <Link Rel="Down" Type="CloudVmReplicaPointList" Href="https://localhost:9398/api/cloud/vmReplicaPoints?format=Entity" />     <Link Rel="Down" Type="CloudReplicaList" Href="https://localhost:9398/api/cloud/replicas?format=Entity" />   </Links> </CloudConnectService> |

With Veeam Backup Enterprise Manager REST API, a tenant can perform the following operations:

* [Start a cloud failover plan](post_cloudfailoverplans_id_start.md)
* [Undo a cloud failover plan](post_cloudfailoverplans_id_undo.md)

A tenant cannot edit a cloud failover plan with Veeam Backup Enterprise Manager REST API.

vCloud Tenant Logon Session Creation

Credentials for the VMware Cloud Director tenant account must be provided in the VCloudOrganizationCredentials element.

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| OrganizationName | String | Name of the vCD organization. | Yes | 1/1 |
| Login | String | Name of the vCD organization user. For details on VMware Cloud Director Tenant Account, see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/backup/cloud/cloud_vcloud_director_tenant.html?ver=120). | Yes | 1/1 |
| Password | String | Password for the vCD organization user account. | Yes | 1/1 |

For example:

|  |
| --- |
| <LoginSpec xmlns="http://www.veeam.com/ent/v1.0">     <VCloudOrganizationCredentials>         <OrganizationName>vCDOrg1</OrganizationName>         <Login>user01</Login>         <Password>Qwe123</Password>     </VCloudOrganizationCredentials> </LoginSpec> |

In the response, Veeam Backup Enterprise Manager will return a representation of the /sessionMngr/ resource with a link to the Cloud Connect service resource. For example:

|  |
| --- |
| <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/362da803-804d-4c32-ad35-0972e432460b">   <Links>     <Link Rel="Up" Type="EnterpriseManager" Href="https://localhost:9398/api/" />     <Link Rel="Down" Type="CloudConnectService" Href="https://localhost:9398/api/cloud" />     <Link Rel="Delete" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/362da803-804d-4c32-ad35-0972e432460b" />   </Links>   <UserName>SRV36\Administrator</UserName>   <SessionId>362da803-804d-4c32-ad35-0972e432460b</SessionId> </LogonSession> |

In the Cloud Connect service resource representation, Veeam Backup Enterprise Manager will return a list of resources with which the specified tenant can work using Veeam Backup Enterprise Manager REST API. For example:

|  |
| --- |
| <CloudConnectService xmlns="http://www.veeam.com/ent/v1.0" Type="CloudConnectService" Href="https://localhost:9398/api/cloud">   <Links>     <Link Rel="Up" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/362da803-804d-4c32-ad35-0972e432460b" />     <Link Rel="Down" Type="CloudFailoverPlanReferenceList" Href="https://localhost:9398/api/cloud/cloudFailoverPlans" />     <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints" />     <Link Rel="Down" Type="CloudReplicaReferenceList" Href="https://localhost:9398/api/cloud/replicas" />     <Link Rel="Down" Type="CloudFailoverPlanList" Href="https://localhost:9398/api/cloud/cloudFailoverPlans?format=Entity" />     <Link Rel="Down" Type="CloudVmReplicaPointList" Href="https://localhost:9398/api/cloud/vmReplicaPoints?format=Entity" />     <Link Rel="Down" Type="CloudReplicaList" Href="https://localhost:9398/api/cloud/replicas?format=Entity" />   </Links> </CloudConnectService> |

With Veeam Backup Enterprise Manager REST API, a tenant can perform the following operations:

* [Start a cloud failover plan](post_cloudfailoverplans_id_start.md)
* [Undo a cloud failover plan](post_cloudfailoverplans_id_undo.md)

A tenant cannot edit a cloud failover plan with Veeam Backup Enterprise Manager REST API.


