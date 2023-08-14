---
title: Personnel File API Endpoint - Schema Employee
tags: [dossier, personnel file, api, connector, endpoint, schema, employee]
keywords: dossier, personnel file, api, connector
last_updated: 2023-08-14
sidebar: guides_sidebar
permalink: personnel_file_api_schema_employee.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

### Employee Schema Endpoint
#### Overview
The '**/v10/schema/employee**' endpoint provides comprehensive schema information regarding the 'employees' within a structured format 
defined by [JSON Schema](https://json-schema.org/specification.html). JSON Schema offers a way to describe the structure of JSON data, making 
it easier for developers to validate and manipulate JSON data structures. In this endpoint, details about each property's attributes — including 
its data type, size, format, and the title that should be utilized when displaying the property — are described in accordance with the 
JSON Schema specification. This approach ensures consistency, clarity, and ease of integration across various systems and applications.

#### GET /v10/schema/employee
##### Required scopes
None
##### Parameters
None
##### Headers
| header                | description                                                                 |
|:----------------------|:----------------------------------------------------------------------------|
| Accept&#8209;Language | Specify the desired language for property titles. Multiple languages are supported. Default: Dutch (nl-NL) |
| Authorization | Include a valid bearer token for authorization |
##### Responses
###### 200 OK - Successful Response
The request was successful, and the schema information is provided in the response.
```
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object",
    "properties": {
        "productCode": {
            "type": "string",
            "title": "Productcombinatie",
            "enum": [
                "BO4GEM",
                "HRERPD",
                "HRSGEM",
                "BO4ASA",
                "PRIASA"
            ]
        },
        "employeeId": {
            "type": "string",
            "title": "Persoonscode",
            "maxLength": 50
        },
        "employeeCode": {
            "type": "string",
            "title": "Persoonsnummer",
            "maxLength": 50
        },
        "initials": {
            "type": "string",
            "title": "Voorletters",
            "maxLength": 15
        },
        "surnamePrefix": {
            "type": "string",
            "title": "Voorvoegsels",
            "maxLength": 15
        },
   ...
}
```
###### 401 Unauthorized - Authorization Failure
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```json
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```

