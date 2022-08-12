---
title: Multipart upload
tags: [publisher, file, upload, multipart, api, library]
keywords: publisher, file, upload, multipart, api, library
summary: A multipart upload request allows you to send metadata along with the data to upload. Use this option if the data you send is small enough to upload again in its entirety if the connection fails. 
last_updated: 10/05/2021
sidebar: guides_sidebar
permalink: guides_file_multipart_upload.html
folder: guides/publishers
topnav: topnav
---

To use multipart upload:

- Create a POST request to the method’s /files URI with the query parameter uploadType=multipart.

Example - POST request multipart

```text
POST https://api.raet.com/mft/v1.0/files?uploadType=multipart
```

- Add the top-level HTTP header: Content-Type. Set to multipart/related, and include the boundary string you're using to identify the different parts of the request

Example - Content-Type header

```text
Content-Type: multipart/related; boundary=foo_bar_baz
```

- Create the body of the request. Format the body according to the multipart/related content type [[RFC 2387]](https://datatracker.ietf.org/doc/html/rfc2387){:target="_blank"}, which contains two parts:

**a) Metadata part**. Must come first, and must have a Content-Type header set to application/json; charset=UTF-8. Add the file's metadata to this part in JSON format. The required metadata fields are:

| Key            | Value            |
| -------------- | ---------------- |
| FileName       | [FileName]       |
| BusinessTypeId | [BusinessTypeId] |

**Note**: For security reasons, file names have some restrictions:

- Filenames should fulfill the following characters sets:

```text
[a-z],[A-Z],[0-9],[-],[_],[.],[(],[)],[,],[$],[+],[`],[=],[']
```

- Malicius file extensions are not allowed


**b) Media part**. Must come second, and should contain the bytes of the files.
Identify each part with a boundary delimiter. [RFC 2046] The boundary delimiter line is defined as a line consisting entirely of two hyphen characters ("-", decimal value 45) followed by the boundary parameter value from the Content-Type header field, optional linear white-space, and a terminating CRLF.
The boundary delimiter MUST occur at the beginning of a line and it is terminated by either the header fields for the next part and two additional CRLFs, or by two additional CRLFs, in case there are no header fields for the next part.
Boundary delimiters must not appear within the encapsulated material, and must be no longer than 70 characters, not counting the two leading hyphens.

Example - Boundary delimiter for Metadata part:

```text
--foo_bar_baz[CRLF]
Content-Type: application/json; charset=UTF-8[CRLF]
[CRLF]
```

Example - Boundary delimiter for Media part:

```text
--foo_bar_baz[CRLF]
[CRLF]
```

The boundary delimiter line following the last body part is a distinguished delimiter that indicates that no further body parts will follow. Such a delimiter line is identical to the previous delimiter lines, with the addition of two more hyphens after the boundary parameter value.

Example - Boundary delimiter for last body part:

```text
--foo_bar_baz--
```

- Send the request:

Example - Send a multipart upload request using the Sandbox Tenant and Sandbox File Type

```text
POST/mft/v1.0/files
?uploadType=multipart HTTP/1.1
Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
Content-Type: multipart/related;boundary=foo_bar_baz

--foo_bar_baz
Content-Type: application/json; charset=UTF-8

{
    "name":"TestFile.txt",
    "businesstypeid":"7100"
}
--foo_bar_baz

This is a test file
--foo_bar_baz--
```

If the request succeeds, the server returns the HTTP 201 Created status code along with the file's metadata:

Example - Response successful request

```text
HTTP/1.1 201
Content-Type: application/json

{
    "id": "7ff1b498-169d-4048-8459-78f7bd7905a3",
    "name": "TestFile.txt",
    "size": 19,
    "creationDate": "2020-02-27T11:03:49.2033291Z",
    "tenantId": "sandbox",
    "businessType": {
    "id": 7100,
    "name": "7100"
},
    "numChunks": 1
}
```

If the request fails, the server returns the HTTP 400, indicating Bad request.

Example - Response failed request

```text
HTTP/1.1 400
Content-Type: application/json

{
    "CorrelationId": "rrt-06f2e934a3cbdb710-a-de-13067-4959526-1",
    "Message": "Error reading body of request. Please, check all the boundaries of the request",
    "ErrorCode": "400",
    "Exception": null
}
```
