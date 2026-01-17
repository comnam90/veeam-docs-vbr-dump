---
title: "PUT /backupServers/{ID}/credentials/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_backupservers_id_creds_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /backupServers/{ID}/credentials/{ID}


Edits a credentials record having specified ID on the backup server with the specified ID.

Request

To edit a credentials record, send the PUT HTTP request to the /backupServers/{ID}/credentials/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the credentials record that must be updated on the backup server. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the elements you want to edit:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Username | String | User name of the edited credentials record in the DOMAIN\USENAME format. | Yes | 0/1 |
| Description | String | Description of the edited credentials record. | Yes | 0/1 |
| Password | String | Password of the edited credentials. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Id": "bc4a63b6-05d1-44f6-b165-1128a33d02c2",   "Username": "VEEAM\\Administrator",   "Description": "Edited with REST API",   "Password": "P@ssw0rd",   "Href": "https://localhost:9398/api/backupServers/fd8fab6c-fca1-4e5c-b485-6d92eb7717bd/credentials/bc4a63b6-05d1-44f6-b165-1128a33d02c2",   "Type": "Credentials"  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 204 No Content.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below updates the password parameter in the credentials record having ID c473b8df-4499-41b8-ba6b-7f76def6fea1 on the backup server with ID f62624c1-8462-4747-8bd4-d686f99b0540.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/credentials/c473b8df-4499-41b8-ba6b-7f76def6fea1    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CredentialsInfo Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/credentials/c473b8df-4499-41b8-ba6b-7f76def6fea1" Type="Credentials" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Id>9a8fb433-cacd-4089-a97e-437e99f128bc</Id>   <Username>VEEAM\Administrator</Username>   <Description>Edited with REST API</Description>   <Password>P@ssw0rd</Password> </CredentialsInfo>    Response:  204 No Content |


