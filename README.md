# Indonesia Food Truck Deventer

Website for Indonesia Food Truck, an authentic Indonesian food truck open every
Monday at the Borgele Winkelcentrum in Deventer, the Netherlands.

Live site content includes:

- Homepage with hours, location, and a call to action
- "Onze Favorieten" — favorite dishes gallery
- Full menu (rames, vegetarian rames, meat dishes, chicken & fish, vegetables,
  side dishes, sandwiches, snacks, drinks) with search and category filters
- A shopping cart that builds a WhatsApp order message
- "Over Ons" / "Ons Verhaal" — about page
- Contact section with phone, email, and social links
- Light/dark theme toggle

## Structure

```
index.html      Single-page site (markup, styles, and app logic)
support.js      Runtime that renders index.html (loads React/ReactDOM/Babel
                from a CDN in the browser and interprets the page's template)
images/         Photos, logo, and favicon used by the site
```

`index.html` is a single self-contained page: the `<x-dc>` block holds the
template, and the `<script type="text/x-dc">` block at the bottom holds the
app logic (menu data, cart handling, navigation, theme toggle). `support.js`
loads React, ReactDOM, and Babel Standalone from a CDN at runtime and uses
them to render the page, so a working internet connection is required for
the site to load correctly.

## Running locally

Any static file server works, e.g.:

```
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser. Opening `index.html` directly
via `file://` will not work because the browser needs to fetch `support.js`
and the CDN scripts over HTTP.

## Deploying

The site is static (`index.html` + `support.js` + `images/`), so it can be
hosted on GitHub Pages, Netlify, Vercel, or any static host by pointing it at
the repository root.

## Editing the menu

Menu items, prices, and descriptions live in the `<script type="text/x-dc">`
block near the bottom of `index.html` (arrays like `vleesItems`,
`groentenItems`, `broodjesItems`, `snacksItems`, and the `priceCatalog` map
used to build WhatsApp order totals). Update an item in both its list and
`priceCatalog` to keep cart totals accurate.
