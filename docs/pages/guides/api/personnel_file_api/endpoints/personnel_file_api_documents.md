---
title: Personnel File API Endpoint - Documents
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-08-15
sidebar: guides_sidebar
permalink: personnel_file_api_documents.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

## Overview
The '**/v10/documents**' endpoint allows for the uploading of new documents to the Personnel File system. When uploading, it's essential to integrate both the document's content and its associated properties within a single request. Depending on the method chosen, the format for sending these details varies. 

## Supported Content Types

To upload a new document both its properties and its content needs to be included within the request. The endpoint accepts either multipart/form-data or multipart/mixed requests.

1. **multipart/form-data**:
   - **Usage:** This format is predominantly used for HTML forms that transmit files, and it
     breaks down the request into various parts.
   - **Properties:** Properties are integrated using form-data fields. Each property becomes a
     separate field, named according to the property it represents.
   - **Document content:** The actual file to be uploaded (PDF, image, etc.) is added as another
     part in the multipart request. The MIME type of the file should be specified in this part's header.
   - **Example:**
        ```
        POST /v10/documents HTTP/1.1
        Host: personnelfile-api.youforce.com
        Authorization: Bearer YOUR_ACCESS_TOKEN
        Content-Type: multipart/form-data; boundary=BOUNDARY_STRING
        
        --BOUNDARY_STRING
        Content-Disposition: form-data; name="CategoryCode"

        4024898-werkvergunning

        --BOUNDARY_STRING
        Content-Disposition: form-data; name="EmployeeId"

        203

        -- BOUNDARY_STRING
        Content-Disposition: form-data;name="document"; filename="vergunning.pdf"
        Content-Type: application/pdf

        [BINARY CONTENT]

        --BOUNDARY_STRING--
        ```
&nbsp;
2. **multipart/mixed**:
   - **Usage**: This MIME type is designed for sending mixed data types in a single message and is versatile
     for various applications, including file uploads with associated metadata.
   - **Properties:** Properties should be encapsulated in a JSON format and placed in the first section of
     the multipart message. This section must have a '**Content-Type**' of '**application/json**'.
   - **Document Content:** This represents the actual file to be uploaded. It's included as the second
     part of the multipart message. The MIME type of the file should be specified in this part's header.
   - **Example:**
        ```
        POST /v10/documents HTTP/1.1
        Host: personnelfile-api.youforce.com
        Authorization: Bearer YOUR_ACCESS_TOKEN
        Content-Type: multipart/mixed; boundary=BOUNDARY_STRING
        
        --BOUNDARY_STRING
        Content-Type: application/json; charset=UTF-8

        {
            "categoryCode": "4024898-werkvergunning",
            "employeeId": "208",
            ...
        }

        --BOUNDARY_STRING
        Content-Type: application/pdf

        [BINARY CONTENT]

        --BOUNDARY_STRING--
        ```

&nbsp;
## POST /v10/documents
### Required scopes
This endpoint requires the '**youforce-personnel-file-api:documents:add**' scope.  
&nbsp;
### Parameters

The parameters are either form-data fields or part of the JSON file. Some of the parameters are required, all others are optional.

| JSON Property | form-data field | Type | Max Length | Required |
|:--------------|:----------------|:-----|-----------:|:---------|
|              1|categoryCode|String|50|Yes| 
|              1|retentionCode|String|50|Yes| 
|              1|employeeId|String|50|Yes| 
|              1|employmentId|String|50|No| 
|              1|startDate|Date||Yes| 
|              1|expirationDate|Date||No| 
|              1|description|String|50|Yes| 
|              1|sourceSystem|String|12|Yes| 
|              1|sourceModule|String|50|Yes| 
|              1|sourceIdentifier|String|50|Yes| 
|              1|contentType|String|Yes|
|              1|special|Boolean|1|No| 
|              1|confidential|Boolean|1|No| 
|              1|expired|Boolean|1|No| 
|              1|custom1|String|30|No| 
|              1|custom2|String|30|No| 
|              1|custom3|String|30|No| 
|              1|file|Base64 or Binary|50 MB|Yes|

&nbsp;
### Responses  
#### 201 Created - Document Created  
The request was successful and the document has been added to the Personnel File. The response returns all properties
of the newly created document.
```
{
    "documentId": "974957",
    "categoryCode": "4024898-werkvergunning",
    "contentType": "application/pdf",
    ...
}
```
&nbsp;
#### 400 Bad Request - Request Validation Failed  
This status code indicates that the server was unable to understand or process the request due
to a client error. The response points to the specific problem.

Note that the language of the errors can be changed by including the '**accept-language**'header. 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "detail": "Invalid document",
    "errors": {
        "SourceIdentifier": [
            "'Source Identifier' must not be empty."
        ],
        "SourceProcess": [
            "'Source Process' must not be empty."
        ]
    }
}
```
&nbsp;
#### 401 Unauthorized - Authorization Failure  
The request lacks an authorization header, the bearer token has expired, or the provided token is invalid.
```
{
    "type": "https://tools.ietf.org/html/rfc7235#section-3.1",
    "title": "Unauthorized",
    "status": 401
}
```
&nbsp;
#### 403 Forbidden - Authorization Denied  
The bearer token does not specify the required scope.
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.3",
    "title": "Forbidden",
    "status": 403
}
```
&nbsp;  
#### 404 Not Found - Employee or Employment Not Found  
The specified employee and/or employment cannot be found.
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "Not found",
    "status": 404,
    "detail": "Employee not found: 208"
}
```
