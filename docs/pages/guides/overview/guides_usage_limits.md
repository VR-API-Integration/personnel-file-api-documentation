---
title: Usage Limits
tags: [getting_started, troubleshooting]
keywords: api, library, api policies
last_updated: 2023-08-23
summary: "We apply usage limits to ensure the availability of our services to all parties interacting with Personnel File. These usage limits depend on your subscription."
sidebar: guides_sidebar
permalink: guides_usage_limits.html
folder: guides/overview
topnav: topnav
---

## Policy

The following policies are determined per registered application:

| Quota                                                    |                             |
| -------------------------------------------------------- |  ---------------------------|
| Max number of Authentication API requests                | 10 requests per 10 seconds  |
| Max number of Personnel File API requests                | 100 requests per minute     |

## API limit

The API limit is the way we protect against traffic spikes. Our APIs and backend can handle a certain amount of traffic, and the API rejects requests that do not conform to the limit. In addition to the request limit the IP-address of the requester will be permanently blocked when the amount exceeds 6.500 requests per 5 minutes.

### Authentication API limit

The limit is set to 10 request per 10 seconds for the same user on the same client. The response will be delayed if there are more than 10 requests within 10 seconds.

### Personnel File API limit

The limit is set to 100 request per minute using a counter. The counter is valid for 1 minute before it is reset, which means that 100 requests in 1 second will result in new requests being rejected for the next 59 seconds.

When you exceed the limit, the API will return response code '429 - Too many requests' and you have to wait for the next time window.
