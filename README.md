# Local 1600 Legislative Dashboard

An automated list of information sources on the legislative topics of the Cook County College Teachers Union, AFT-IFT Local 1600: news, podcasts, government reports, press releases, bill status changes and changes to key webpages.

**This dashboard is the result of an automated search. Sources are not approved or endorsed by CCCTU Local 1600.**

## How it works

- `index.html` is the whole site: the topic pages (Illinois and federal, in priority order), All sources, Archive and About.
- `data/` holds the content the page reads:
  - `topics.json`: the 17 topics in priority order
  - `bills.json`: tracked bills and their latest status
  - `items.json`: source items (headline, outlet, date, link, original 2–3 sentence summary, type, topics, colleges)
  - `meta.json`: when the last scan finished
- A scheduled scan runs every morning at about 8:30 a.m. Central, updates the files in `data/`, and commits them. Each day's changes appear in the commit history.
- Items older than four weeks move to the Archive page automatically.

## Hiding an item

To take an item off the site, open `data/items.json` on GitHub, find the item, change it to include `"hidden": true`, and commit. The next scan leaves hidden items alone.

## Hosting

The site is served by GitHub Pages from the `main` branch (Settings → Pages → Deploy from a branch → `main` / root).

## Colleges and Local 1600 tabs

`data/colleges.json` lists the 14 colleges plus the City Colleges of Chicago system, with official names, districts, locations and Local 1600 chapters. The daily scan reads it but never rewrites it; edit it by hand if a name or chapter changes. College and Local 1600 items live in `data/items.json` like every other item (tagged by `colleges` and `mentionsLocal1600`), and you hide them the same way.

## Bills page

`data/bills.json` holds each bill's status plus a plain-language `summary`, `changes` (amendments), `effect` (which colleges it applies to), `stage` (1 Introduced … 6 Law, shown as the progress bar), `nextStep` and `nextDate`. The daily scan keeps these current. `data/sessions.json` lists the legislative sessions for the Bills page's session selector, with each session's end date and a note on remaining session days; the scan adds a new session when the first bill of the 105th General Assembly or 120th Congress appears.
