---
title: Implementation details
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

Use taostats in your Vibe coding/ bot creation.

[https://mcp.taostats.io/](https://mcp.taostats.io/)

# What is MCP?

Large Language Models (LLMs) are trained on data.  But, it does not know everything - what if the pages are not indexed?  What if the data is private?

A Model Context Protocol (MCP) fixes that.  It tells your LLM - "here is some specialized information that will help you answer questions."  MCPS are often used by developers"

* Database access: if claude code or Copilot actually know the tables, and the data in the tables - it won't spit out code with "fill in the details" - it will fill in the details
* Proproietary information:  Chatbots for insurance companies can look up your account - and claim status.  The shipping bot can track your order.  These wouldn't be in e normal LLM context, but the MCP gives access to that data.

# Taostats MCP

Your LLM will not know the balance of wallet 5Hd2ze5ug8n1bo3UCAcQsf66VNjKqGos8u6apNfzcU86pg4N.  It changes minute by minute.

But if you add in the taostats MCP - the LLM can look for the taostats account endpoint - call the endpoint, and tell you that the balance is 508,379.9377 (accurate as of 2/16/2026 0947 EST).

* Alerting bots - sorted
* Trading bots - data is sorted (be careful!)
* Bittensor app building - sorted.

Al you need is an API key and to follow the setup instructions!
