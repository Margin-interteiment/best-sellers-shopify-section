# Best sellers — Shopify section

Custom Shopify section **"Best sellers"** built from scratch (no theme snippets reused).

## Files

| File | Purpose |
|------|---------|
| `sections/best-sellers.liquid` | Section markup + schema (settings & blocks) |
| `assets/best-sellers.css` | Section styles (scoped, BEM) |
| `assets/best-sellers.js` | Tab switching, wishlist modal, Ajax cart |

## Features

- **Blocks → collections** (limit 3). Each `Collection` block has:
  - `Collection` (collection picker)
  - `Collection title` (text) — overrides the default collection name
  - `Product` (product picker) — overrides the first product of the collection
- **Section settings:** `Section label` (text), `Title` (text).
- First block is **active by default**; one tab is **always active** (an active tab can't be toggled off).
- Clicking a collection name swaps the product shown in the right column.
- **Product card:**
  - Featured image via `<picture>` with a smaller image for mobile and `1x`/`2x` densities.
  - `placeholder_svg_tag` fallback when the product has no image.
  - Up to **3 tags**, styled like the base `New` badge; a `Sale` tag is red.
  - Image and product title link to the product page.
  - Price with strikethrough compare-at price.
- **Wishlist (heart):** opens a ~450px modal — `"[PRODUCT NAME] has been added to the your wishlist."` — with dark overlay, scroll lock, close via the X button or overlay click (Esc also closes).
- **Add to cart (eye):** adds the first available variant via the **Shopify Ajax Cart API** (`/cart/add.js`). Disabled when the product is sold out.

## Install

Copy the three files into a Shopify theme (`sections/` and `assets/`), then in the
theme editor add the **Best sellers** section and configure its blocks.

Or with the Shopify CLI:

```bash
shopify theme push --only sections/best-sellers.liquid \
  --only assets/best-sellers.css --only assets/best-sellers.js
```
