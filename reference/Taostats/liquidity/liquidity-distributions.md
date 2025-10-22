---
title: Get Liquidity Distribution
excerpt: A breakdown of the liquidity at every price tick.
api:
  file: taostats-1.json
  operationId: get_apidtaoliquiditydistributionv1
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## Response example

Showing a segment of price with different active liquidities.

```
...

{
      "activeLiquidity": "1440957321",
      "price": "0.0483229580117229056229522940"
    },
    {
      "activeLiquidity": "1440957321",
      "price": "0.0488085874110689833991748318"
    },
    {
      "activeLiquidity": "1440957321",
      "price": "0.0492990972217808558704205053"
    },
    {
      "activeLiquidity": "1440957321",
      "price": "0.0497945364903436235075979460"
    },
    {
      "activeLiquidity": "91240979464",
      "price": "0.0502949547561429888846537086"
    },
    {
      "activeLiquidity": "91240979464",
      "price": "0.0508004020564187411750832081"
    },
...
```