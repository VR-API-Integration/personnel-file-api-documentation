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

| Quota                                                    |                                                              |
| -------------------------------------------------------- |  --------------------------------------------------------------------- |
| Max number of Authentication API calls                   | 10 calls per 10 seconds (6.500 calls per 5 min results in IP-block)    |
| Max number of Personnel File API calls                   | 100 calls per minute                                                   |

## API limit

The API limit is the way we protect against traffic spikes. Our APIs and backend can handle a certain amount of traffic, and the API rejects requests that do not conform to the limit.

### Authentication API limit

The limit is set to 10 request per 10 seconds for the same user on the same client. The repsonse will be delayed if there are more than 10 requests within 10 seconds. Additionally the IP-address will be permanently blocked when the number of requests exceed 6.500 per 5 minutes. 

### Personnel File API limit

The Personnel File API limit is the way we protect against traffic spikes. Our APIs and backend can handle a certain amount of traffic, and the API rejects requests that do not conform to the limit.

The limit is set to 100 request per minute using a counter. The counter is valid for 1 minute before it is reset, which means that 100 requests in 1 second will result in new requests being rejected for the next 59 seconds.

When you exceed the limit, the API will return response code '429 - Too many requests' and you have to wait for the next time window.
