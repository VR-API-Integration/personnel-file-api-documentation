---
title: Getting Started
sidebar: guides_sidebar
permalink: guides_getting_started.html
folder: guides/overview
summary: Follow these instructions to learn how to start integrating with the Youforce API using the sandbox tenant.
---

This section has been prepared to give the developer a quick guide to start consuming the Youforce API. The specific example is about IAM domain, but same principles can be applied to any of the other domains including Extensions.

As a precondition, this guides assumes the developer has a proper application created, which is linked to the specific API to be consumed, and the following information is available:

- Client-id
- Client-secret
- Tenant-id



**Step 1: Download the example Postman collection [OPTIONAL]**

Each of the available domains has an available example Postman collection containing the very basic methods a developer needs to start using our APIs. This step is optional, but it should facilitate the next steps.

You can find the proper Postman collection under the corresponding option in the left menu of this documentation.


**Step 2: Request an access token**

In order to make the necessary calls to retrieve the expected information from the HR Core system, a token needs to be requested.

This token will give you access to a particular tenant in a specific application. Hence, this step will require knowing the client-id, client-secret and tenant-id.

In case of using he example Postman collection, it will be enough to edit the default variables to contain the actual values. See screenshot:



Otherwise, the required information will have to be added in the corresponding parameters.



Once this call is executed, a valid token should be received.



Another advantage of using the example Postman collection, is that the token will get automatically stored in a variable, so it can be easily used for the next calls to the actual API.




**Step 3: Make the test call to the desired endpoint**

Now we are in a position to directly call the needed endpoint. This example is using the Persons one for IAM domain, but any other get method can be used in a similar way.

Notice that, as mentioned in previous step, if the example Postman collection is being used, the token information will already be available in the AccessToken variable set in the Authorization header, otherwise, the token information should be manually added in the same header.

This should be enough to successfully run the method in the API.




We hope this section was useful. Thanks for building an integration using Youforce API.
