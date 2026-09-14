# Turun vihreiden ratikkatuotteet

A fully static GitHub Pages product page for selling ratikkatuotteet with
Stripe-hosted checkout.

## Recommended Stripe setup

Use **Stripe Payment Links**. This keeps the site static, requires no backend,
and lets Stripe collect payment, receipts, shipping address, shipping rates, tax
settings, and order details.

The current site points every buy button to one shared Payment Link:

```html
https://buy.stripe.com/14AdR2cwE6fGbji6WAbAs00?locale=fi
```

If the Stripe checkout URL changes later, replace the Payment Link in every
Stripe `href` in `index.html`.

## Selling existing Stripe products

1. In Stripe Dashboard, open **Product catalog**.
2. Confirm each existing product has an active one-time EUR Price:
   - T-paita: max. 25 EUR
   - Huppari: max. 40 EUR
   - Kangaskassi: max. 15 EUR
3. Create one Payment Link and add those existing Prices.
4. Enable adjustable quantities for each line item.
5. Enable billing and shipping address collection.
6. Add shipping rates, automatic receipts, and the payment methods you want.
7. Add custom fields for fulfillment choices:
   - `Koko` as a dropdown, for example `S`, `M`, `L`, `XL`, `XXL`
   - `Vari` as a dropdown for available colors
   - `Lisatiedot` as optional text for special notes, if needed
8. Copy the Payment Link URL into every Stripe link in `index.html`.

## Selling new products

1. In Stripe Dashboard, create the Product first.
2. Add a one-time EUR Price.
3. Add that Price to the same Payment Link if it should be sold with the current
   products.
4. If a new product needs separate choices that do not fit the shared custom
   fields, create a dedicated Payment Link for that product and update only that
   product card's `href` in `index.html`.

## Easy solution choices

**Best default:** one shared Payment Link with all products and adjustable
quantities. This is easiest for customers who want more than one product.

**Best for complex variants:** one Payment Link per product. Use this if each
product has different size/color rules or if fulfillment gets confusing in a
shared checkout.

**Best for inventory per size/color:** create separate Stripe Prices for each
variant, or move to a small backend using Stripe Checkout Sessions. Payment
Links are simpler, but variant-level stock control is limited.

## GitHub Pages

Serve the repository from the root directory in GitHub Pages. The site has no
build step and no runtime dependencies.

## Local preview

Open `index.html` in a browser, or serve the directory with any static server.
