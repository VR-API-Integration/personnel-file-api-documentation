---
title: Personnel File API Endpoint - Employees
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-08-15
sidebar: guides_sidebar
permalink: personnel_file_api_employees.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

## Overview
The '**/v10/employees**' endpoint is used within the Personnel File system to query employees and their associated employments. It's a key tool for locating the correct employee when you need to upload a new document, ensuring that the information is tied to the proper individual and employment record.
&nbsp;
## GET /v10/employees
### Required scopes
This endpoint requires the '**youforce-personnel-file-api:employees:list**' scope.
&nbsp;
## Parameters

| parameter | type | description |
|:----------|:-----|:------------|
| top | query | The maximum number of employees to return |
| search | query | A search expression |
| filter | query | A filter expression |

> **Note: make sure to URL encode the search and filter parameters**
&nbsp;
### Example requests
```
GET /v10/employees?top=10&search=jans%20OR%20vries
Host: personnelfileapi.youforce.com
Accept-Language: en-GB
Authorization: Bearer YOUR_ACCESS_TOKEN

GET /v10/employees?top=5&filter=dateOfBirth%20lt%201950-01-01
Host: personnelfileapi.youforce.com
Accept-Language: en-GB
Authorization: Bearer YOUR_ACCESS_TOKEN
```
&nbsp;
### Responses
#### 200 OK - Successful Response
The request was successful and returns the employees that match the query. The list may be empty.
```
[
    {
        "productCode": "HRERPD",
        "employeeId": "10030490",
        "employeeCode": "600",
        "initials": "H",
        "surnamePrefix": "de",
        "surname": "Vries",
        "dateOfBirth": "1968-09-01",
        "birthnamePrefix": "de",
        "birthname": "Vries",
        "gender": "V",
        "organizationalUnit": "Metatech Nederland - Metatech Administratie BV",
        "employments": [
            {
                "employmentId": "-",
                "startDate": "1995-03-01",
                "departmentCode": "10641458",
                "departmentAbbr": "AFDICT",
                "departmentName": "afdeling ICT",
                "jobTitle": "#1CC#"
            }
        ]
    }
]
```
&nbsp;
#### 400 Bad Request - Request Validation Failed
This status code indicates that the server was unable to understand or process the request due to client error. The particular response provided here suggests that a validation error occurred while interpreting the request, and it points to the specific problem within the request's syntax.

In this case, the response detail '**"Syntax error at position 14 in 'dateOfBirth la 1950-01-01'."**' identifies the exact position and content of the error, enabling developers to diagnose and correct the issue. The use of a standard RFC 7231 reference for "Bad Request" also aligns with established HTTP status code definitions, ensuring clarity and adherence to common web protocols.
```
&nbsp;
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "Bad Request",
    "status": 400,
    "detail": "Syntax error at position 14 in 'dateOfBirth la 1950-01-01'."
}
```
&nbsp;
#### 401 Unauthorized - Authorization Failure
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```
&nbsp;
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```
&nbsp;
#### 403 Forbidden - Authorization Denied
The bearer token does not specify the required scope.
```json
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.3",
    "title": "Forbidden",
    "status": 403
}
```
