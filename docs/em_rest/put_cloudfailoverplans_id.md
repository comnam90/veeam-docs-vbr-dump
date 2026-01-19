---
title: "PUT /cloud/cloudFailoverPlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_cloudfailoverplans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /cloud/cloudFailoverPlans/{ID}


Edits a cloud failover plan that has the specified ID.

Request

To edit a cloud failover plan, send the PUT HTTP request to the /cloud/cloudFailoverPlans/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the cloud failover plan that must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| PostFailoverPlanCommandEnabled | Boolean | Defines whether custom post-failover script is specified for the cloud failover plan. Possible values:   * True * False | Yes | 0/1 |
| PostFailoverPlanCommand | String | Path to the custom post-failover script, for example: C:\scripts\post-failover.bat | Yes | 0/1 |
| PreFailoverPlanCommandEnabled | Boolean | Defines whether custom pre-failover script is specified for the cloud failover plan. Possible values:   * True * False | Yes | 0/1 |
| PreFailoverPlanCommand | String | Path to the custom pre-failover script, for example: C:\scripts\pre-failover.bat. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "TenantUid": "urn:veeam:CloudTenant:b25f5f1d-a3c3-45ed-af23-9ef31a94dac7",   "TenantName": "ABC Company",   "Description": "Cloud failover plan for ABC Company full site failover",   "CloudFailoverPlanOptions": {     "PostFailoverPlanCommandEnabled": true,     "PostFailoverPlanCommand": "C:\\scripts\\post-failover.bat",     "PreFailoverPlanCommandEnabled": true,     "PreFailoverPlanCommand": "C:\\scripts\\pre-failover.bat"   },   "CloudFailoverPlanInfo": {     "Includes": {}   },   "Name": "ABC Company Failover Plan",   "UID": "urn:veeam:CloudFailoverPlan:e7ca6822-a87f-443d-8aae-8005970543bf",   "Href": "https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?format\u003dEntity",   "Type": "CloudFailoverPlan"  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below updates the post-failover script parameter in the cloud failover plan that has ID e7ca6822-a87f-443d-8aae-8005970543bf.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudFailoverPlan Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?format=Entity" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverPlan:e7ca6822-a87f-443d-8aae-8005970543bf" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <TenantUid>urn:veeam:CloudTenant:b25f5f1d-a3c3-45ed-af23-9ef31a94dac7</TenantUid>   <TenantName>ABC Company</TenantName>   <Description>Cloud failover plan for ABC Company full site failover</Description>   <CloudFailoverPlanOptions>     <PostFailoverPlanCommandEnabled>true</PostFailoverPlanCommandEnabled>     <PostFailoverPlanCommand>C:\scripts\post-failover.bat</PostFailoverPlanCommand>     <PreFailoverPlanCommandEnabled>false</PreFailoverPlanCommandEnabled>     <PreFailoverPlanCommand/>   </CloudFailoverPlanOptions>   <CloudFailoverPlanInfo>     <Includes>       <CloudFailoverPlanVm Type="CloudFailoveredVm" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf/includes/231a6e3e-09e6-4641-9322-40898fcb966a">         <FailoverPlanVMId>231a6e3e-09e6-4641-9322-40898fcb966a</FailoverPlanVMId>         <Name>srv38</Name>         <Order>0</Order>       </CloudFailoverPlanVm>       <CloudFailoverPlanVm Type="CloudFailoveredVm" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf/includes/096a7d0a-c92a-4da4-9302-4416b2fe929f">         <FailoverPlanVMId>096a7d0a-c92a-4da4-9302-4416b2fe929f</FailoverPlanVMId>         <Name>srv40</Name>         <Order>1</Order>       </CloudFailoverPlanVm>     </Includes>   </CloudFailoverPlanInfo> </CloudFailoverPlan>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>UpdateFailoverPlan</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>UpdateFailoverPlan</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


