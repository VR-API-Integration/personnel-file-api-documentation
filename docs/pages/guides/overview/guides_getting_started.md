---
title: Getting Started
sidebar: guides_sidebar
permalink: guides_getting_started.html
folder: guides/overview
summary: Quick guide to start consuming Personnel File API.
---

This section has been prepared to give the developer a quick guide to start consuming the Personnel File API. 

This guide is written under the assumption that the developer has a proper application created and available, which should be linked to the specific API to be consumed, and that the following information is known:

- Client-id
- Client-secret
- Tenant-id



### Step 1: Download the example Postman collection [OPTIONAL]

Each of the available domains has an available example Postman collection, containing the very basic methods a developer needs to start using our APIs. This step is optional, but it would facilitate the next steps.

You can find the proper Postman collection under the corresponding option in the left menu of this documentation.
<br />

### Step 2: Request an access token

In order to make the necessary calls to retrieve the expected information from Personnel File, a token needs to be requested.

This token will provide access to a particular tenant in a specific application. Hence, this step will require knowing the client-id, client-secret and tenant-id.

In the case of using the example Postman collection, it will be enough to update the existing variables with the actual values, as displayed in the image below.

<kbd>
{% include image.html file="postman_variables.png" alt="Getting started"  %}
</kbd>
<br />
The values of these variables will be used to request a new token.

<div style="border: 1px solid black">
{% include image.html file="postman_token_parameters.png" alt="Getting started"  %}
</div>
<br />
<br />

Once the request for a token is executed using the button 'Get New Access Token', a valid token should be received.

<div style="border: 1px solid black">
{% include image.html file="postman_received_token.png" alt="Getting started" %}
</div>
<br />
<br />
Use the button 'Use Token' to apply this token to the collection. This token will be stored in a variable that is used in the headers of all requests. If the token is expired the request will fail and you can request a new token again in the same way.

<div style="border: 1px solid black">
{% include image.html file="postman_token_in_header.png" alt="Getting started"  %}
</div>
<br />

### Step 3: Make the test call to the desired endpoint

Now we are able to directly call the needed endpoint. This example is requesting a list of available document types (categories), but any other get method can be used in a similar way.

Notice that, as mentioned in previous step, if the example Postman collection is being used, the token information will already be available in the AccessToken variable set in the Authorization header, otherwise, the token information should be manually added in the same header.

This should be enough to successfully run the method in the API.
<div style="border: 1px solid black">
{% include image.html file="postman_categories_response.png" alt="Getting started"  %}
</div>
<br />
<br />

We hope this section was useful. Thanks for building an integration using Personnel File API.
