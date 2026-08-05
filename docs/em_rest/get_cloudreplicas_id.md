---
title: "GET /cloud/replicas/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudreplicas_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/replicas/{ID}


Returns a resource representation of a cloud replica that has the specified ID. The replica is created by the tenant whose account is created on the backup server connected to Veeam Backup Enterprise Manager.

The replica can be one of the following types:

* Regular replica for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replica
* VMware Cloud Director CDP replica

Request

To get a replica, send the GET HTTP request to the /cloud/replicas/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/replicas/{ID} |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /cloud/replicas/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the cloud replica resource, for example: urn:veeam:CloudReplica:8393c284-c953-403f-a9b9-cff63e0c6815. |
| Name | String | Name of the cloud replica resource, for example: ABC Company Servers Replication. |
| Platform | String | Platform for which the replication job is created. Possible values:   * VMware * HyperV  * vCloud |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudReplica](get_query_cloudreplica.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server of the Service Provider. |
| /cloud/replicas/{ID} | Alternate | Alternate URL of the [/cloud/replicas/{ID}](cloudreplicas_id.md) resource. |
| /cloud/replicas/vmReplicaPoints | Down | URL of the [/cloud/replicas/{ID}/vmReplicaPoints](cloudreplicas_id_vmreplicapoints.md) resource — a collection of restore points for separate tenant VMs in the cloud replica. |

Example

The example below returns an entity resource representation of a replica that has ID ec1f1bba-c39b-420f-839a-9ace1a716a36.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/replicas/ec1f1bba-c39b-420f-839a-9ace1a716a36?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <CloudReplica xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/cloud/replicas/ec1f1bba-c39b-420f-839a-9ace1a716a36?format=Entity" Type="CloudReplica" Name="Replication Job 1" UID="urn:veeam:CloudReplica:ec1f1bba-c39b-420f-839a-9ace1a716a36" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/replicas/ec1f1bba-c39b-420f-839a-9ace1a716a36" Name="Replication Job 1" Type="CloudReplicaReference" Rel="Alternate" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/replicas/ec1f1bba-c39b-420f-839a-9ace1a716a36/vmReplicaPoints" Type="CloudVmReplicaPointReferenceList" Rel="Down" />     </Links>     <Platform>VMware</Platform> </CloudReplica> |

Page updated 2026-07-29

