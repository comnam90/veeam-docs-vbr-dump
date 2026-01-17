---
title: "POST /backupServers?action=create"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_backupservers.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /backupServers?action=create


Connects a backup server to Veeam Backup Enterprise Manager.

Request

To connect a backup server to Veeam Backup Enterprise Manager, send the POST HTTP request to the /backupServers?action=create resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/backupServers?action=create |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the backup server that you want to connect. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Description | String | Description of the backup server. | Yes | 1/1 |
| DnsNameOrIpAddress | String | DNS name or IP address of the backup server. | Yes | 1/1 |
| Port | String | Port over which Veeam Backup Enterprise Manager must communicate with the backup server. By default, port 9392 is used. | Yes | 1/1 |
| Username | String | User name of the account to connect to the backup server specified in the DOMAIN\USERNAME or HOST\USERNAME format, for example: 172.16.13.119\Administrator. | Yes | 1/1 |
| Password | String | Password of the account to connect to the backup server. | Yes | 1/1 |
| WcfPort | UShort | Default certificate port used by Veeam Backup Enterprise Manager for collecting data from backup servers that have Veeam Backup & Replication 12 or later installed, for example: 9405. | Yes | 0/1 |
| VbrCertificateThumbprint | String | Certificate thumbprint of the backup server. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Description": "Veeam backup server in Columbus",   "DnsNameOrIpAddress": "172.16.13.119",   "Port": 9392,   "Username": "172.16.13.119\\Administrator",   "Password": "1234",   "VbrCertificateThumbprint": "0000000000000000000000000000000000000000",   "WcfPort": 9405  } |

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

The example below connects a backup server having IP address 172.16.13.119 to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  POST https://localhost:9398/api/backupServers?action=create    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml  Request Body:  <?xml version="1.0" encoding="utf-8"?> <BackupServerSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Description>Veeam backup server 01</Description>   <DnsNameOrIpAddress>172.16.13.119</DnsNameOrIpAddress>   <Username>172.16.13.119\Administrator</Username>   <Port>9392</Port>   <Password>1234</Password>   <WcfPort>9405</WcfPort>   <VbrCertificateThumbprint>0000000000000000000000000000000000000000</VbrCertificateThumbprint> </BackupServerSpec>    Response:  201 Success    Response Body:  None |


