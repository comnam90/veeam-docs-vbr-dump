---
title: "put_cdppolicies_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_cdppolicies_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Edits a CDP policy having the specified ID.

Request

To edit a CDP policy, send the PUT HTTP request to the /cdpPolicies/{ID} URL.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the edited CDP policy. The body of the request must conform to the  [XML Schema Definitionem\_rest\_](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

|  |
| --- |
| Note |
| In the request body, you can send all resource properties or only those properties that you want to edit. |

The request body must contain the elements you want to edit. You can define the following general parameters for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Description | String | Description provided for the CDP policy. | Yes | 0/1 |
| ScheduleConfigured | Boolean | Defines whether scheduling options are configured for the CDP policy. | Yes | 0/1 |
| ScheduleEnabled | Boolean | Defines whether scheduling options are enabled for the CDP policy. If you set this option to True, you need to specify the PolicyScheduleOptions element. | Yes | 0/1 |
| NextRun | DateTime | Date and time of the next CDP policy run. The parameter accepts only UTC-formatted DateTime values. | Yes | 0/1 |
| PolicyScheduleOptions | PolicyScheduleOptions | Defines scheduling options for the CDP policy. For details, see [CDP Policy Scheduling Options](#schedule). | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Href": "https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce?format=Entity",   "Type": "CdpPolicy",   "Name": "CDP Policy 1",   "UID": "urn:veeam:CdpPolicy:145f3365-6ec0-44e9-9538-8c8c34ebdcce",   "xmlns": "http://www.veeam.com/ent/v1.0",   "Description": "Created by TECH\\sheila.d.cory",   "ScheduleConfigured": "true",   "ScheduleEnabled": "true"  } |

CDP Policy Scheduling Options

You can define the following scheduling options for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| RecoveryPointObjectiveSeconds | Int64 | Recovery point objective in seconds. | Yes | 0/1 |
| RecoveryPointObjectiveMinutes | Int64 | Recovery point objective in minutes. | Yes | 0/1 |
| RPOSchedule | RPOSchedule Type | Time intervals that define when the CDP policy is allowed to create a replicated state of the source VMs. For details, see [RPO Schedule Options](#rpo). | Yes | 0/1 |
| RPOReporting | RPOReporting Type | Defines RPO reporting settings. For details, see [RPO Reporting Options](#reporting). | Yes | 0/1 |
| ShortTermRetentionMinutes | Int64 | Time period for which short-term restore points must be stored, in minutes. |  |  |
| ShortTermRetentionHours | Int64 | Time period for which short-term restore points must be stored, in hours. |  |  |
| LongTermRetentionHours | Int64 | Defines how often new long-term restore points must be created, in hours. |  |  |
| LongTermRetentionKeepDays | Int64 | Defines for how long the long-term restore points must be retained, in days. | Yes | 0/1 |
| LongTermRetentionSchedule | LongTermRetentionSchedule Type | Time intervals that define when the CDP policy must create application-consistent and when crash-consistent long-term restore points. For details, see [Long-Term Retention Schedule Options](#long_term). | Yes | 0/1 |

RPO Schedule Options

RPO schedule options are provided in the following format:

XML Representation

|  |
| --- |
| <RPOSchedule Enabled="true">   <TimePeriods>     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>   </TimePeriods> </RPOSchedule> |

JSON Representation

|  |
| --- |
| "RPOSchedule": {   "Enabled": "true",   "TimePeriods": {     "Day": [       {         "Name": "Sunday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Monday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Tuesday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Wednesday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Thursday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Friday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Saturday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       }     ]   }  } |

You can define the following RPO schedule options for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether RPO schedule options are specified for the CDP policy. | Yes | 1/1 |
| TimePeriods | TimePeriods Type | Defines an hourly scheme by which the CDP policy must run. The schedule scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the CDP policy must run, 0 means the CDP policy must not run. | Yes | 0/unbounded |

RPO Reporting Options

RPO reporting options are provided in the following format:

XML Representation

|  |
| --- |
| <RPOReporting>   <MarkAsWarning>     <Enabled>true</Enabled>     <RPOThresholdSeconds>2</RPOThresholdSeconds>     <RPOThresholdMinutes>0</RPOThresholdMinutes>   </MarkAsWarning>   <MarkAsFailed>     <Enabled>true</Enabled>     <RPOThresholdSeconds>3</RPOThresholdSeconds>     <RPOThresholdMinutes>0</RPOThresholdMinutes>   </MarkAsFailed> </RPOReporting> |

JSON Representation

|  |
| --- |
| "RPOReporting": {   "MarkAsWarning": {     "Enabled": "true",     "RPOThresholdSeconds": "2",     "RPOThresholdMinutes": "0"   },   "MarkAsFailed": {     "Enabled": "true",     "RPOThresholdSeconds": "3",     "RPOThresholdMinutes": "0"   }  } |

You can define the following RPO reporting options for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether RPO reporting options are specified for the job. | Yes | — |
| MarkAsWarning | CDPReplicaRPOReporting WarningOptionsType | Time interval in seconds or minutes before Veeam Backup & Replication sends a notification with a warning if a newly created restore point is not transferred to the target within the set RPO. For details, see [Warning Settings](#warning). | Yes | 0/1 |
| MarkAsFailed | CDPReplicaRPOReporting FailedOptionsType | Time interval in seconds or minutes before Veeam Backup & Replication sends a notification with an error if a newly created restore point is not transferred to the target within the set RPO. For details, see [Error Settings](#error). | Yes | 0/1 |

Warning Settings:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether warning notifications are enabled. | Yes | — |
| RPOThresholdSeconds | Int | Time interval in seconds before Veeam Backup & Replication sends a notification with a warning if a newly created restore point is not transferred to the target within the set RPO. | Yes | 0/1 |
| RPOThresholdMinutes | Int | Time interval in minutes before Veeam Backup & Replication sends a notification with a warning if a newly created restore point is not transferred to the target within the set RPO. | Yes | 0/1 |

Error Settings:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether error notifications are enabled. | Yes | — |
| RPOThresholdSeconds | Int | Time interval in seconds before Veeam Backup & Replication sends a notification with an error if a newly created restore point is not transferred to the target within the set RPO. | Yes | 0/1 |
| RPOThresholdMinutes | Int | Time interval in minutes before Veeam Backup & Replication sends a notification with an error if a newly created restore point is not transferred to the target within the set RPO. | Yes | 0/1 |

Long-Term Retention Schedule Options

Long-term retention schedule options are provided in the following format:

XML Representation

|  |
| --- |
| <LongTermRetentionSchedule Enabled="true">   <TimePeriods>     <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>     <Day Name="Monday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>     <Day Name="Tuesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>     <Day Name="Wednesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>     <Day Name="Thursday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>     <Day Name="Friday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>     <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>   </TimePeriods> </LongTermRetentionSchedule> |

JSON Representation

|  |
| --- |
| "LongTermRetentionSchedule": {   "Enabled": "true",   "TimePeriods": {     "Day": [       {         "Name": "Sunday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       },       {         "Name": "Monday",         "#text": "2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2"       },       {         "Name": "Tuesday",         "#text": "2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2"       },       {         "Name": "Wednesday",         "#text": "2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2"       },       {         "Name": "Thursday",         "#text": "2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2"       },       {         "Name": "Friday",         "#text": "2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2"       },       {         "Name": "Saturday",         "#text": "1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"       }     ]   }  } |

You can define the following periodic scheduling options for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines whether long-term retention schedule options are specified for the job. | Yes | — |
| Schedule | TimePeriods Type | Defines an hourly scheme when the CDP policy must create application-consistent and when crash-consistent long-term restore points. The scheduling scheme is constructed by the following pattern:  <Day Name ="Sunday"> 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>  where 1 means the CDP policy must create crash-consistent long-term restore points, 2 means the CDP policy must create application-consistent long-term restore points. | Yes | 0/1 |

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

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

Example

The example below changes the settings of the CDP policy having ID 8846d24b-d12f-4b7a-94e2-8c78241b841.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/jobs/78c3919c-54d7-43fe-b047-485d3566f11f?action=edit    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CdpPolicy xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e?format=Entity" Type="CdpPolicy" Name="CDP Policy Cloud Director" UID="urn:veeam:CdpPolicy:8846d24b-d12f-4b7a-94e2-8c78241b841e" xmlns="http://www.veeam.com/ent/v1.0">   <PolicyType>CdpReplica</PolicyType>   <Platform>vCloud</Platform>   <Description />   <ScheduleEnabled>true</ScheduleEnabled>   <NextRun>2023-02-13T11:18:16.989527Z</NextRun>   <PolicyScheduleOptions>     <CdpReplica>       <RecoveryPointObjectiveSeconds>15</RecoveryPointObjectiveSeconds>       <RecoveryPointObjectiveMinutes>0</RecoveryPointObjectiveMinutes>       <RPOSchedule>         <TimePeriods>           <Day Name="Sunday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Monday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Tuesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Wednesday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Thursday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Friday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>           <Day Name="Saturday">1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1</Day>         </TimePeriods>       </RPOSchedule>       <RPOReporting>         <MarkAsWarning>           <Enabled>true</Enabled>           <RPOThresholdSeconds>2</RPOThresholdSeconds>           <RPOThresholdMinutes>0</RPOThresholdMinutes>         </MarkAsWarning>         <MarkAsFailed>           <Enabled>true</Enabled>           <RPOThresholdSeconds>3</RPOThresholdSeconds>           <RPOThresholdMinutes>0</RPOThresholdMinutes>         </MarkAsFailed>       </RPOReporting>       <ShortTermRetentionMinutes>0</ShortTermRetentionMinutes>       <ShortTermRetentionHours>4</ShortTermRetentionHours>       <LongTermRetentionHours>8</LongTermRetentionHours>       <LongTermRetentionKeepDays>7</LongTermRetentionKeepDays>       <LongTermRetentionSchedule Enabled="true">         <TimePeriods>           <Day Name="Sunday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Monday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Tuesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Wednesday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Thursday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Friday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>           <Day Name="Saturday">2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2</Day>         </TimePeriods>       </LongTermRetentionSchedule>     </CdpReplica>   </PolicyScheduleOptions>   <CdpPolicyInfo>     <CdpReplicaPolicyInfo>       <Includes>         <ObjectInJob Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e/includes/e198ca81-9750-452d-a3ee-c1bc3806a537" Type="ObjectInJob">           <ObjectInJobId>e198ca81-9750-452d-a3ee-c1bc3806a537</ObjectInJobId>           <HierarchyObjRef>urn:vCloud:Vapp:1903878c-230d-456d-80d2-4df9e319b6d7.urn:vcloud:vapp:aff5d61d-4481-4f72-a019-e0ed1bbd63a3</HierarchyObjRef>           <Name>vApp-TS</Name>           <DisplayName>vApp-TS</DisplayName>           <GuestProcessingOptions>             <VssSnapshotOptions>               <VssSnapshotMode>RequireSuccess</VssSnapshotMode>               <IsCopyOnly>true</IsCopyOnly>               <UsePersistentGuestAgent>false</UsePersistentGuestAgent>             </VssSnapshotOptions>             <WindowsCredentialsId />             <LinuxCredentialsId />           </GuestProcessingOptions>         </ObjectInJob>         <ObjectInJob Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e/includes/e406d018-c019-4daa-a18a-6d48ca3db0e2" Type="ObjectInJob">           <ObjectInJobId>e406d018-c019-4daa-a18a-6d48ca3db0e2</ObjectInJobId>           <HierarchyObjRef>urn:vCloud:Vapp:1903878c-230d-456d-80d2-4df9e319b6d7.urn:vcloud:vapp:1b86c2dd-d85c-4f03-b05e-841562425c8b</HierarchyObjRef>           <Name>vApp02</Name>           <DisplayName>vApp02</DisplayName>           <GuestProcessingOptions>             <VssSnapshotOptions>               <VssSnapshotMode>RequireSuccess</VssSnapshotMode>               <IsCopyOnly>false</IsCopyOnly>               <UsePersistentGuestAgent>false</UsePersistentGuestAgent>             </VssSnapshotOptions>             <WindowsCredentialsId />             <LinuxCredentialsId />           </GuestProcessingOptions>         </ObjectInJob>       </Includes>       <GuestProcessingOptions>         <WindowsCredentialsId />         <LinuxCredentialsId />       </GuestProcessingOptions>     </CdpReplicaPolicyInfo>   </CdpPolicyInfo> </CdpPolicy>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-3">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-3" />   </Links>   <TaskId>task-3</TaskId>   <State>Running</State>   <Operation>EditCdpPolicy</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-3    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-3">   <Links>     <Link Rel="Delete" Href="https://localhost:9398/api/tasks/task-3" />   </Links>   <TaskId>task-3</TaskId>   <State>Finished</State>   <Operation>EditCdpPolicy</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
