# Northline Tee

A fully static one-product T-shirt shop for GitHub Pages, with checkout handled
by Stripe Payment Links.

## Stripe setup

1. Create a Stripe Product and Price for the T-shirt.
2. Create a Payment Link for that price.
3. Add a required custom dropdown field:
   - Label: `Size`
   - Options: `S`, `M`, `L`, `XL`
4. Enable shipping address collection, shipping rates, automatic receipts, and
   the payment methods you want to accept.
5. Replace the placeholder URL in `index.html`:

```html
https://buy.stripe.com/REPLACE_WITH_YOUR_PAYMENT_LINK
```

## GitHub Pages

Serve the repository from the root directory in GitHub Pages. The site has no
build step and no runtime dependencies.

## Local preview

Open `index.html` in a browser, or serve the directory with any static server.
