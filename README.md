# The Maker's Price Bench

A free pricing calculator for handmade sellers. Static site â€” one HTML file, no build step,
no dependencies, no server.

**Live:** https://price-bench-weld.vercel.app

## What it does

Most handmade pricing formulas multiply cost by four and ignore marketplace fees. This one
solves backwards through the fee stack to find the price that nets a target profit, then
reports the seller's true hourly rate at that price.

The core calculation, where `k` is the combined percentage fee rate charged on the order total:

```
order total = (target profit + flat fees + shipping cost + true cost) / (1 - k)
item price  = order total - shipping charged to buyer
```

Dividing rather than multiplying is the whole point â€” a percentage fee charged on the final
price cannot be covered by adding that percentage on top.

## Deploying

Vercel, or any static host. There is no build command and no framework. Point it at this
directory and serve `index.html`.

## Before going live

Search and replace these placeholders in `index.html`:

| Placeholder | Appears | Replace with |
|---|---|---|
| `price-bench-weld.vercel.app` | 2Ã— | Your real domain, for the canonical and Open Graph tags |
| `REPLACE-WITH-YOUR-GUMROAD-OR-ETSY-LINK` | 1Ã— | The purchase link for the full edition |

The canonical and Open Graph URLs matter for search indexing and for how the page previews
when shared â€” leaving the placeholder in costs you both.

## Notes

- All calculation runs client-side. No inputs are transmitted or stored.
- Fee presets reflect published rates at time of writing and are all user-editable, since
  marketplaces change them.
- Light and dark themes are token-based and follow the visitor's system setting, with a
  manual override.
