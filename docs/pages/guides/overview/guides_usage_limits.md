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
| Authentication calls                                     | 400 authentication calls per month                                    |
| Max number of API calls per minute                       | 100 calls per minute                                                  |

## API limit

The API limit is the way we protect against traffic spikes. Our APIs and backend can handle a certain amount of traffic, and the API rejects requests that do not conform to the limit.

The limit is set to 100 request per limit using a counter. The counter is valid for 1 minute before it is rest, which means that 100 request in 1 second will result in requests being rejected for the next 59 seconds.

When you exceed the limit, the API will return response code '429 - Too many requests' and you have to wait for the next time window.
