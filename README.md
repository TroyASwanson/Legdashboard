# Local 1600 Legislative Dashboard

An automated list of information sources on the legislative topics of the Cook County College Teachers Union, AFT-IFT Local 1600: news, podcasts, government reports, press releases, bill status changes and changes to key webpages.

**This dashboard is the result of an automated search. Sources are not approved or endorsed by CCCTU Local 1600.**

## How it works

- `index.html` is the whole site: the topic pages (Illinois and federal, in priority order), All sources, Archive and About.
- `data/` holds the content the page reads:
  - `topics.json`: the 16 topics in priority order
  - `bills.json`: tracked bills and their latest status
  - `items.json`: source items (headline, outlet, date, link, original 2–3 sentence summary, type, topics, colleges)
  - `meta.json`: when the last scan finished
- A scheduled scan runs every morning at about 8:30 a.m. Central, updates the files in `data/`, and commits them. Each day's changes appear in the commit history.
- Items older than four weeks move to the Archive page automatically.

## Hiding an item

To take an item off the site, open `data/items.json` on GitHub, find the item, change it to include `"hidden": true`, and commit. The next scan leaves hidden items alone.

## Hosting

The site is served by GitHub Pages from the `main` branch (Settings → Pages → Deploy from a branch → `main` / root).
