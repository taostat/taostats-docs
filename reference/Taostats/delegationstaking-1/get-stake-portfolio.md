---
title: Get Stake Portfolio
excerpt: This endpoint requires a PRO subscription
api:
  file: taostats-1.json
  operationId: get_apidtaostake_balanceportfoliov1
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
```json response example
   {
      "hotkey_name": "Taostats",
      "hotkey": {
        "ss58": "5GKH9FPPnWSUoeeTJp19wVtd84XqFW4pyK2ijV2GsFbhTrP1",
        "hex": "0xbc0e6b701243978c1fe73d721c7b157943a713fca9f3c88cad7a9f7799bc6b26"
      },
      "coldkey": {
        "ss58": "5Dw9eWw19H1n6VtK4WLTJVgk5XNhXgHV39pTptthWSLjG31w",
        "hex": "0x52b5527a846824c4095e7688e6cf1271a9c6b36f5b6391e82928c2b36be11a59"
      },
      "netuid": 64,
      "subnet_rank": 283,
      "subnet_total_holders": 14051,
      "balance": "532854877505",
      "balance_as_tao": "45028348418",
      "total_bought_alpha": "566189540885",
      "total_bought_alpha_as_tao": "142999900000",
      "total_bought_alpha_as_usd": "59017.06",
      "total_sold_alpha": "179216171419",
      "total_sold_alpha_as_tao": "45041577328",
      "total_sold_alpha_as_usd": "18642.43",
      "total_transferred_in_alpha": "0",
      "total_transferred_in_alpha_as_tao": "0",
      "total_transferred_in_alpha_as_usd": "0",
      "total_transferred_out_alpha": "0",
      "total_transferred_out_alpha_as_tao": "0",
      "total_transferred_out_alpha_as_usd": "0",
      "total_buys": 2,
      "total_sells": 1,
      "total_transfers_in": 0,
      "total_transfers_out": 0,
      "current_market_price_usd": "37.77",
      "current_market_price_tao": "0",
      "average_purchase_price_tao": "0",
      "average_sale_price_tao": "0",
      "average_purchase_price_usd": "104.24",
      "average_sale_price_usd": "104.02",
      "total_earned_alpha": "145881508039",
      "total_earned_alpha_as_tao": "12327566725",
      "total_earned_alpha_as_usd": "5510.09",
      "realised_profit_usd": "-38.26",
      "unrealised_profit_usd": "-20209.90",
      "realised_profit_tao": "-222230533",
      "unrealised_profit_tao": "-52707739023",
      "period_start_tao_price_in_usd": null,
      "period_start_alpha": null,
      "period_start_alpha_price_in_tao": null,
      "period_start_alpha_cost_in_usd": null
    }
```