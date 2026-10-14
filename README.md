# Malaysia Health Questionnaires Directory

Source for <https://questionnaires.drakmal.com/>, a searchable directory of health questionnaires
developed, translated or validated in Malaysia. Static site on GitHub Pages; no build step on the host.

## Files

- `index.html` - the whole page (inline CSS and JS, no external dependencies).
- `data.js` - generated data (`window.MHQ`). Do not edit by hand.
- `CNAME` - custom domain for GitHub Pages (`questionnaires.drakmal.com`).

## Updating the data

`data.js` is generated from the newest `Malaysia_Health_Questionnaires_Directory*.xlsx` in the
parent folder by `build_site.py` (kept outside this repo, next to the workbooks):

    python build_site.py

The script drops Borderline rows, takes article/access URLs from the cell hyperlinks, and
recounts the Tool access "Entries" column over the published rows. It stops with an error if the
column headers change or the row count differs from `EXPECTED_ROWS`. Commit and push the new
`data.js` (and bump `lastmod` in `sitemap.xml`) to redeploy.
