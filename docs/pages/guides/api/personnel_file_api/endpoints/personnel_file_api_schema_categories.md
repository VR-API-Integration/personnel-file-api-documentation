---
title: Personnel File API Endpoint - Schema - Categories
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-08-15
sidebar: guides_sidebar
permalink: personnel_file_api_schema-categories.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

### Overview
Within the Personnel File, documents are organized into pre-defined categories. The '**/v10/schema/categories**' endpoint 
offers insights into these classifications by furnishing a comprehensive list of categories, each identified by a unique code and title.

> The Personnel File empowers each tenant with full authority over the categories relevant to their organization, allowing for
> customization of both codes and titles.
 
### GET /v10/schema/categories
#### Required scopes
None
#### Parameters
None
#### Headers

| header                | description                                                                 |
|:----------------------|:----------------------------------------------------------------------------|
| Accept&#8209;Language | Specify the desired language for property titles. Multiple languages are supported. Default: Dutch (nl-NL) |
| Authorization | Include a valid bearer token for authorization |

#### Example Request
```
GET /v10/schema/categories HTTP/1.1
Host: personnelfileapi.youforce.com
Accept-Language: en-GB
Authorization: Bearer YOUR_ACCESS_TOKEN
```

#### Responses
##### 200 OK - Successful Response
The request was successful, and the schema information is provided in the response.
```
[
    {
        "code": "4024898-werkvergunning",
        "title": "Work permit"
    },
    {
        "code": "4024898-sollicitatie",
        "title": "Job Application"
    },
    {
        "code": "4024898-bigRegistratie",
        "title": "Dutch BIG registration"
    },
    {
        "code": "4024898-vrij008",
        "title": "Freely available 8"
    },
    {
        "code": "4024898-verklaringGedrag",
        "title": "Certificate of good conduct"
    },
    {
        "code": "4024898-scanPersoonlijk",
        "title": "Scanned personal"
    },
    {
        "code": "4024898-vaccinaties",
        "title": "Vaccinations"
    },
    ...
]
```
##### 401 Unauthorized - Authorization Failure
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```json
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```

### Get /v10/schema/categories/{categoryCode}
#### Required scopes
None
#### Parameters

| parameter | type | description |
|:----------|:-----|:------------|
| categoryCode | path | code of the category to be returned |

#### Example request
```
GET /v10/schema/categories/4024898-sollicitatie
Host: personnelfileapi.youforce.com
Accept-Language: en-GB
Authorization: Bearer YOUR_ACCESS_TOKEN
```

#### Responses
##### 200 OK - Successful Response
The request was successful, and the schema information is provided in the response.
```json
{
    "code": "4024898-sollicitatie",
    "title": "Job Application"
}
```
##### 401 Unauthorized - Authorization Failure
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```json
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```
##### 404 Not found - Category Not Found
The requested category does not exist.
```json
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.4",
    "title": "Not Found",
    "status": 404
}
```
