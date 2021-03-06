# Get tenantsecurescores

Retrieve your historical Secure Score data for a specified (n) number of days.

The data set returned can be adjusted using the period field which is an integer value between 1 and 90, defined as number of days.

If you entered 1 you would retrive 1 days history of Secure Score data from todays date, if you entered 90, you would retrieve 90 days history of Secure Score data from todays date. 

## Prerequisites
The following **scopes** are required to execute this API: Reports.Read.All

The following **roles** are able to execute this API: TenantAdmin, SecurityAdmin, HelpdeskAdmin, ExchangeAdmin, SharePointAdmin, UserAccountAdmin

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /reports/getTenantSecureScores(period=)/content
```
## Optional query parameters
None

## Request headers
| Name       | Type | Description|
|:-----------|:------|:----------|
| Authorization  | string  | Bearer <token>. Required. |

## Request body
/getTenantSecureScores(period=)/content
## Response
If successful, this method returns a 200 OK response code version object and collection of score data objects for every Secure Score control in the response body.
## Error
If unsuccessful, this method returns a 400 Bad Request code. For example if period ranges outside 1-90 are chosen.
## Response Content Definitions
tenantId              : (GUID) Your tenant ID

createdDate           : (STRING) YYYY; MM; DD

licensedUserCount     : (INT) Licensed users

activeUserCount       : (INT) Active users

secureScore           : (INT) Your Secure Score

maxSecureScore        : (INT) Your maximum attainable Secure Score

accountScore          : (INT) Your Secure Score for Account Controls

dataScore             : (INT) Your Secure Score for Data Controls

deviceScore           : (INT) Your Secure Score for Device Controls

enabledServices       : (STRING) Collection of Strings, showing enabled Tenant Services

controlScores         : (STRING) Dictionary(String, Object). Contains control specific information. For e.g. for adminMFA control it will have 2 values. The total number of administrators and number of admins that don’t have MFA enabled. The entries in controlDetails will change per control.

averageSecureScore    : (DOUBLE) Average O365 Secure Score

averageMaxSecureScore : (DOUBLE) Average O365 Maximal Attainable O365 Secure Score

averageAccountScore   : (DOUBLE) Average O365 Secure Score for Account Controls

averageDataScore      : (DOUBLE) Average O365 Secure Score for Data Controls

averageDeviceScore    : (DOUBLE) Average O365 Secure Score for Device Controls

## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "get_application"
}-->
```http
GET https://graph.microsoft.com/v1.0/reports/getTenantSecureScores(period=1)/content
```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.application"
} -->
```
HTTP/1.1 200 OK
Content-type: application/json

{
  "tenantId": "12bce6d0-bfeb-4a82-abe6-98ccf3196a11",
  "createdDate": "2017-01-31",
  "licensedUserCount": 28,
  "activeUserCount": 0,
  "secureScore": 92,
  "maxSecureScore": 271,
  "accountScore": 39,
  "dataScore": 53,
  "deviceScore": 0,
  "enabledServices": [
    "HasExchange",
    "HasLync",
    "HasSharePoint",
    "HasOD4B"
  ],
  "controlScores": [
    {
      "referenceId": "AdminMFA",
      "score": 8,
      "maxScore": 50,
      "controlDetails": null
    },
    {
      "referenceId": "UserMFA",
      "score": 7,
      "maxScore": 30,
      "controlDetails": null
    },
    {
      "referenceId": "AltInfoIncomplete",
      "score": 1,
      "maxScore": 1,
      "controlDetails": null
    },
    {
      "referenceId": "DLPEnabled",
      "score": 20,
      "maxScore": 20,
      "controlDetails": null
    }
  ],
  "averageSecureScore": 19.1315212,
  "averageMaxSecureScore": 261.859253,
  "averageAccountScore": 4.38279533,
  "averageDataScore": 14.6059513,
  "averageDeviceScore": 0.142776
}


```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get tenantsecurescores",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
