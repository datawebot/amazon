# Amazon coverage

## Coverage and prerequisites

This is the single repository for Amazon across **20 configured marketplaces**;
country-specific repositories are not needed. The catalog and adapters inspected
for this guide contain the following domains for search and product details:

| Country | Code | Domain |
| --- | --- | --- |
| United States | US | amazon.com |
| Singapore | SG | amazon.sg |
| Japan | JP | amazon.co.jp |
| United Kingdom | GB | amazon.co.uk |
| Germany | DE | amazon.de |
| France | FR | amazon.fr |
| Australia | AU | amazon.com.au |
| Italy | IT | amazon.it |
| Spain | ES | amazon.es |
| Canada | CA | amazon.ca |
| United Arab Emirates | AE | amazon.ae |
| Saudi Arabia | SA | amazon.sa |
| Egypt | EG | amazon.eg |
| Türkiye | TR | amazon.com.tr |
| Mexico | MX | amazon.com.mx |
| Poland | PL | amazon.pl |
| Sweden | SE | amazon.se |
| Netherlands | NL | amazon.nl |
| Belgium | BE | amazon.com.be |
| Ireland | IE | amazon.ie |

**Qualification:** configuration is not a guarantee of current production
availability or successful extraction in every country. Recorded sampling on
2026-10-27 found usable search pages in the ten added markets (AE, SA, EG, TR,
MX, PL, SE, NL, BE, IE), but Saudi Arabia and Egypt product-page samples contained
no product data and are handled as failures, not empty successes. India, Brazil
and South Africa are not included. No fresh customer end-to-end acceptance was
run for this guide.

The examples below use Amazon US. Before using another market, discover its
exact domain and confirm endpoint IDs, allowed hosts, input schemas and current
availability. Preserve marketplace URLs, currencies and locale information; do
not infer source support from shopping-search coverage.

You need a datawebot account with approved email sign-in, API access and enough
credits. Source availability and maintenance can change; live discovery is
authoritative. Read the [terms](https://www.datawebot.com/terms) and use data only
where you have the necessary rights.

| Operation | Endpoint ID shown in the public site guide |
| --- | --- |
| Search | `amazon.search_items` |
| Product details | `amazon.product_details` |

These are reference IDs, not a substitute for discovery. Confirm them before
running work, and use the returned contracts rather than guessing IDs.

Search URLs use `/s?k=URL_ENCODED_KEYWORD`; product URLs use `/dp/ASIN`
or `/gp/product/ASIN`. Use an observed product URL rather than inventing an ASIN.
Start with `max_pages: 1`; use only parameters allowed by discovery.
No search filters or full-catalogue extraction are promised.
