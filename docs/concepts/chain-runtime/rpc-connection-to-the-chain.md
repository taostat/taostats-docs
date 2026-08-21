---
title: how RPC works:
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---

How do you extract knowledge from the Bittensor chain? The [taostats API](/api-reference/#/)  gets you 99.9% of the way there.

There are some calls that may require direct access into the chain.  There is a [Python SDK](https://github.com/opentensor/bittensor) for some direct access. But not even that gets you everything.

The [Taostats RPC Connection](/api-reference/) gives you direct access into the chain.  From the chain you can make many requests for granular information.

> 📘 **The latest methods available from the Substrate RPC**

See the [API documentation](/api-reference/) for endpoint details.

With just an API key from taostats, you can make RPC calls using the [Bittensor SDK](https://docs.learnbittensor.org/sdk/bt-api-ref)
