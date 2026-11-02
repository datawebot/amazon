# Amazon examples for every configured country

The same self-contained scripts work with the marketplace URL you supply.
They do not silently rewrite other countries to amazon.com.

| Country | Code | Search URL for ETL / MCP |
| --- | --- | --- |
| United States | US | `https://www.amazon.com/s?k=coffee` |
| Singapore | SG | `https://www.amazon.sg/s?k=coffee` |
| Japan | JP | `https://www.amazon.co.jp/s?k=coffee` |
| United Kingdom | GB | `https://www.amazon.co.uk/s?k=coffee` |
| Germany | DE | `https://www.amazon.de/s?k=coffee` |
| France | FR | `https://www.amazon.fr/s?k=coffee` |
| Australia | AU | `https://www.amazon.com.au/s?k=coffee` |
| Italy | IT | `https://www.amazon.it/s?k=coffee` |
| Spain | ES | `https://www.amazon.es/s?k=coffee` |
| Canada | CA | `https://www.amazon.ca/s?k=coffee` |
| United Arab Emirates | AE | `https://www.amazon.ae/s?k=coffee` |
| Saudi Arabia | SA | `https://www.amazon.sa/s?k=coffee` |
| Egypt | EG | `https://www.amazon.eg/s?k=coffee` |
| Türkiye | TR | `https://www.amazon.com.tr/s?k=coffee` |
| Mexico | MX | `https://www.amazon.com.mx/s?k=coffee` |
| Poland | PL | `https://www.amazon.pl/s?k=coffee` |
| Sweden | SE | `https://www.amazon.se/s?k=coffee` |
| Netherlands | NL | `https://www.amazon.nl/s?k=coffee` |
| Belgium | BE | `https://www.amazon.com.be/s?k=coffee` |
| Ireland | IE | `https://www.amazon.ie/s?k=coffee` |

For example, collect Germany's search page:

```sh
python3 examples/market-analysis-etl/python.py 'https://www.amazon.de/s?k=coffee' de-coffee-001 work/de
node examples/llm-agent/node.mjs 'https://www.amazon.de/s?k=coffee' de-mcp-coffee-001
```

For [price matching](price-matching/) or [inventory alerts](inventory-alerts/),
select a product URL returned by that country's search and keep its marketplace
domain. Use `/dp/ASIN` or `/gp/product/ASIN`, not a made-up product ID.
Currencies and prices come from returned data, not the country table.

[Coverage qualifications](../docs/coverage.md) still apply: these are 20 configured
markets, not 20 newly passed live acceptance tests. In recorded sampling,
Saudi Arabia and Egypt product pages lacked product data; those runs must fail
rather than create a price or stock signal. India, Brazil and South Africa are
not included.
