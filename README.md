# The Maker's Price Bench

A free pricing calculator for handmade sellers. Static site — one HTML file, no build step,
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

Dividing rather than multiplying is the whole point — a percentage fee charged on the final
price cannot be covered by adding that percentage on top.

## Deploying

Vercel, or any static host. There is no build command and no framework. Point it at this
directory and serve `index.html`.

Deployments are linked to this repository, so pushing to the default branch publishes.

## Outstanding

The purchase button in the upgrade section is currently a disabled "coming soon" state,
because the product is not yet listed for sale. Once it has a URL, swap this line in
`index.html`:

```html
<span class="buy is-soon" aria-disabled="true">Full version coming soon <span class="price-tag">$12</span></span>
```

back to:

```html
<a class="buy" href="YOUR-PURCHASE-URL">Get the full version <span class="price-tag">$12</span></a>
```

If a custom domain is added later, update the `canonical` and `og:url` tags in the document
head, which currently point at the `.vercel.app` address.

## Notes

- All calculation runs client-side. No inputs are transmitted or stored.
- Fee presets reflect published rates at time of writing and are all user-editable, since
  marketplaces change them.
- Light and dark themes are token-based and follow the visitor's system setting, with a
  manual override.
- The paid edition is deliberately kept outside this repository. Do not add it — a public
  repo would serve it for free.
