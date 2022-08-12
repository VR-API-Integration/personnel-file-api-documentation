---
title: Getting Started
sidebar: guides_sidebar
permalink: guides_getting_started.html
folder: guides/overview
summary: Follow these instructions to learn how to upload and download files with the File API using the sandbox tenantId and Sandbox File Types.For a better understanding, see also our Getting Started Video on Youtube.
---

## Create Sandbox Application

### 1. Create account in the Youforce developer portal

- [Youforce developer portal](https://developers.youforce.com){:target="_blank"}

### 2. Create new File API Sandbox App

{% include image.html file="create_fileapi-app.png" url="/images/create_fileapi-app.png" alt="Create new File API Sandbox App" %}

### 3. Retrieve credentials (Api Key, Secret key)

{% include image.html file="retrieve_credentials.png" url="/images/retrieve_credentials.png" alt="Retrieve credentials"%}

## Get Access Token

### 1. Send request to Authentication API

The Authentication API is used to obtain the required access token. The request must include the content type header and the HTTP body must include the required Client Credentials.

```shell
curl -X POST 
 'https://api.raet.com/authentication/token'
 -H 'Cache-Control: no-cache' 
 -H 'Content-Type: application/x-www-form-urlencoded' 
 -d 'client_secret=xxxxxxx&client_id=xxxxxxxx&grant_type=client_credentials'
```

Below, a response example containing the access token and the expiration time which is 2 hours. After that time Apps need to re-authenticate to get a new access token.

```javascript
{
    'access_token':'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...',
    'token_type': 'BearerToken',
    'expires_in': '7200',
}
```

## Send request to File API Endpoint including the access token

App must use the Authorization header containing the access token. The API always operates within the scope of one HR Core client, also called tenant. An API call cannot retrieve data from multiple tenants.

By default,sandbox apps are authorized to the Sandbox File Types:

| Business Type Id | Name                       | Authorization |
| ---------------- | -------------------------- | ------------- |
| 7100             | File API Sandbox Uploads   | Publisher     |
| 7101             | File API Sandbox Downloads | Subscriber    |

Below, a request example for listing sandbox files:

```shell
curl -X GET 
 'https://api.raet.com/requests/v1.0/files/%fileid%?role=subscriber' 
 -H 'Cache-Control: no-cache' 
 -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...'
 -H 'x-raet-tenant-Id: sandbox'
```

## Authentication Error Response

The error payload shown below, describes the 401 error response Apps will receive in case of any authentication error.

```javascript
{
    'message': 'Authentication Error',
    'correlationId': 'rrt-0d027480041e2a148-a-de-7885-572449-1',
    'issuedAt': '2018-03-27T07:44:25.554Z',
    'errorCode': 'unauthorized',
    'statusCode': 401
}
 ```

Miss use reasons for having authentication errors are:

* Wrong credentials
* Expired credentials
* Unauthorized access tokens
* Expired access tokens

For more detailed information please refer to the request headers & responses section

## File API Endpoints

Once you have a valid access token you can perform below actions as publisher of the file types:

* Upload
* List uploaded files
* Download uploaded files

As subscriber of the file types you can perform below actions:

* List Available Files
* Download 
* Delete

In case you have any question or doubt during the integration, you can reach us through the Visma Developer Community in Slack. See our Support page for more information. 
