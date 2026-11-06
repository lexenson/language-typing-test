# Language Typing Test

Typing practice for **Greek** and **Portuguese** (PT/BR): timed tests, translations under or after each word, optional voice, personal bests, progress charts and per-word stats.

Both languages have word categories: the 2,000 most common words in sets of 100 (1–100, 101–200, … 1901–2000) and Harry Potter vocabulary. Greek also has prefix and starting-letter sets. The Portuguese top 2,000 is ranked from [wordfreq](https://github.com/rspeer/wordfreq) data, grouped by dictionary form and checked by hand. Words spelled differently in Portugal and Brazil (equipa/equipe, facto/fato, comboio/trem) follow the PT/BR switch.

It's a single static page (`index.html`) with no build step.

## Stats

Results and word stats are saved in the visitor's own browser (localStorage), so every user has their own stats and nothing is sent anywhere.

To move stats to another browser or device, use **Export stats** at the bottom of the page, then **Import stats** on the other one. Importing merges with what's already there and never creates duplicates, so it's safe to do more than once.

## Hosting

Served by GitHub Pages from the `main` branch (root folder). Every push to `main` redeploys automatically within a minute or two.

To run locally, open `index.html` in a browser, or run `python3 -m http.server` in this folder and visit http://localhost:8000.
