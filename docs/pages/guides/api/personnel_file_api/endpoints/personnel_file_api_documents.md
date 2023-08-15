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

### Overview
The '**/v10/documents**' endpoint allows for the uploading of new documents to the Personnel File system. When uploading, it's essential to integrate both the document's content and its associated properties within a single request. Depending on the method chosen, the format for sending these details varies. 

### Supported Content Types

To upload a new document both its properties and its content needs to be included within the request. The endpoint accepts either multipart/form-data or multipart/mixed requests.

1. **multipart/form-data**:
   - **Usage:** This format is predominantly used for HTML forms that transmit files, and it
     breaks down the request into various parts.
   - **Properties:** Properties are integrated using form-data fields. Each property becomes a
     separate field, named according to the property it represents.
   - **Document content:** The actual file to be uploaded (PDF, image, etc.) is added as another
     part in the multipart request. The MIME type of the file should be specified in this part's header.

2. **multipart/mixed**:
   - **Usage**: This MIME type is designed for sending mixed data types in a single message and is versatile
     for various applications, including file uploads with associated metadata.
   - **Properties:** Properties should be encapsulated in a JSON format and placed in the first section of
     the multipart message. This section must have a '**Content-Type**' of '**application/json**'.
   - **Document Content:** This represents the actual file to be uploaded. It's included as the second
     part of the multipart message. The MIME type of the file should be specified in this part's header.

### POST /v10/documents
#### Required scopes
This endpoint requires the '**youforce-personnel-file-api:documents:add**' scope.

### Parameters

The parameters are either form-data fields or part of the JSON file. Some of the parameters are required, all others are optional.

| Name | Type | Required | Description |
|:-----|:-----|:---------|:------------|
