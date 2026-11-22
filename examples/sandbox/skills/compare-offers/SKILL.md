---
name: compare-offers
description: Use whenever comparing an offer to the state of the art.
---

# Compare offers recommendation

## When to use

Use this skill when you want to compare an offer to the state of the art.

## Workflow

1. Get the content of the offer by using the `read_offer_file_tool`.
2. Use the `tavily_search` tool to research each offer for state of the art and prices.
3. Create a detailed markdown report about the offer, pros and cons, and your search result about price and state of the art. 
