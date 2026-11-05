# Language Typing Test

Typing practice for **Greek** and **Portuguese** (PT/BR): timed tests, translations under or after each word, optional voice, personal bests, progress charts and per-word stats.

It's a single static page (`index.html`) with no build step.

## Stats

Results and word stats are saved in the visitor's own browser (localStorage), so every user has their own stats and nothing is sent anywhere.

To move stats to another browser or device, use **Export stats** at the bottom of the page, then **Import stats** on the other one. Importing merges with what's already there and never creates duplicates, so it's safe to do more than once.

## Hosting

Served by GitHub Pages from the `main` branch (root folder). Every push to `main` redeploys automatically within a minute or two.

To run locally, open `index.html` in a browser, or run `python3 -m http.server` in this folder and visit http://localhost:8000.
