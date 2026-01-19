---
title: "HTTP Authentication"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/http_authentication.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# HTTP Authentication


Every work cycle with Veeam Backup Enterprise Manager REST API must begin with the client logon. The logon procedure includes the following steps:

1. The client sends an unauthorized GET HTTP request to the base URL of Veeam Backup Enterprise Manager REST API:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/ |

1. In the response body, the server returns links for creating a new logon session:

|  |
| --- |
| Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

1. The client sends the POST HTTP requests to the obtained URL to create a new logon session.

In the header of the POST HTTP request, the client must provide the username and password of the account to be used for authentication. The account must have one of the following roles in Veeam Backup Enterprise Manager:

* Portal Administrators
* Portal Users
* Restore Operators

For logon, Veeam Backup Enterprise Manager REST API uses the [Basic HTTP Authentication](http://www.ietf.org/rfc/rfc2617.txt). For example, if the client uses the account with the following credentials:

* Username: User
* Password: Password

the client must compose the User:Password base64 encoded:

|  |
| --- |
| VXNlcjpQYXNzd29yZA== |

The Username:Password pair is supplied in the Authorization header to the POST HTTP request. In the value of the header, the client must prepend Basic before the Username:Password pair:

|  |
| --- |
| Authorization: Basic VXNlcjpQYXNzd29yZA== |

1. The server analyzes the provided credentials and checks if the specified account has the Portal Administrator, Portal User or Restore Operator role in Veeam Backup Enterprise Manager.

* If the provided credentials are valid and logon has been successful, the server creates a new authentication token and returns it to the client with a representation of a new logon session.
* If the provided credentials are not valid or the Authorization header is missing, the server returns a 401 Unauthorized error in response. The server also returns the WWW-Authenticate header indicating the authorization scheme to be used, for example:

|  |
| --- |
| WWW-Authenticate: Basic Realm=RestSvc |

1. If logon is successful, the server returns the created authentication token in the X-RestSvcSessionId header of the response. The client must obtain the returned authentication token and add it to the header of every subsequent request to the server.

|  |
| --- |
| X-RestSvcSessionId: OsU6RL7OGkGKrPBGxKxURw== |

In addition, Veeam Backup Enterprise Manager REST API returns the cookie token in the Set-Cookie header of the response. The cookie token is kept in the client. If HTTP cookies are enabled for the client, the client can automatically take the authentication token from the cookie and add it to every request to Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Set-Cookie: X-RestSvcSessionId=OsU6RL7OGkGKrPBGxKxURw==; Path=/api; |

If the client is set to send the authentication token both from the HTTP header and from the cookie, Veeam Backup Enterprise Manager REST API will use the cookie token and ignore the token sent in the X-RestSvcSessionId header of the request.

Timeout Value for Idle Sessions

The timeout value for an idle logon session is 15 minutes. If the client sends no requests to the server for 15 minutes, the current session token expires. To continue working with Veeam Backup Enterprise Manager REST API, the client must obtain a new authentication token from the server.

Logout

To log out, the client must delete a created logon session. A URL for a session deletion is provided in the representation of the logon session resource:

|  |
| --- |
| <Link Rel="Delete" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/d4130a8b-3f5a-4999-8a33-b02c7ff4b441" /> |

|  |
| --- |
| Tip |
| For an example of the logon and logout procedures, see [Beginner Example](beginner_example.md). |


