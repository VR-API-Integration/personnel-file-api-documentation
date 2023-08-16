---
title: Personnel File API Endpoint - Schema - Retention
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-08-15
sidebar: guides_sidebar
permalink: personnel_file_api_schema_retention.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

## Overview
The Personnel File manages the retention of documents through one or more retention schedules defined by the 
administrator of the Personnel File. The '**/v10/schema/retention**' endpoint lists these retention schedules
so documents can be assigned to one of these schedules.

## GET /v10/schema/retention
### Required scopes
None
### Parameters
None
### Headers

| header                | description                                                                 |
|:----------------------|:----------------------------------------------------------------------------|
| Accept&#8209;Language | Specify the desired language for property titles. Multiple languages are supported. Default: Dutch (nl-NL) |
| Authorization | Include a valid bearer token for authorization |

&nbsp;
### Example Request
```
GET /v10/schema/retention HTTP/1.1
Host: personnelfileapi.youforce.com
Accept-Language: en-GB
Authorization: Bearer YOUR_ACCESS_TOKEN
```
&nbsp;
### Responses
#### 200 OK - Successful Response
The request was successful, and the schema information is provided in the response.
```json
{
    "schedules": {
        "DEFAULT": "Default schedule",
        "CUSTOM": "Custom schedule"
    }
}
```

&nbsp;
#### 401 Unauthorized - Authorization Failure
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```json
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```
