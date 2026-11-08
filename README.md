# Language Typing Test

Typing practice for **Greek** and **Portuguese** (PT/BR): timed tests, translations under or after each word, optional voice, personal bests, progress charts and per-word stats.

Both languages have word categories: the most common words in sets of 100 (1–100, 101–200, …; 2,000 for Greek, 4,000 for Portuguese) and Harry Potter vocabulary. Greek also has prefix and starting-letter sets. The Portuguese top 4,000 is ranked from [wordfreq](https://github.com/rspeer/wordfreq) data, grouped by dictionary form and checked by hand. Words spelled differently in Portugal and Brazil (equipa/equipe, facto/fato, comboio/trem) follow the PT/BR switch.

It's a single static page (`index.html`) with no build step.

## Stats

Results and word stats are always saved in the visitor's own browser (localStorage), so the site works without an account and offline.

### Sync across devices (optional)

With Firebase configured, every visitor gets a silent anonymous account, and **Sign in with Google to sync** (next to Personal bests) upgrades it. Every device signed in to the same Google account then shares results and word stats. On sign-in, this browser's stats are merged in: results are combined without duplicates, and word counts are kept per device and added up. Signing out leaves the stats in the browser.

Data lives in Firestore under `users/<uid>/data/`: `typing-<lang>-<yyyymm>` (results per month), `typing-meta` (when history was cleared) and `wc_<lang>` (word counts per device).

One-time setup in the [Firebase console](https://console.firebase.google.com) (free Spark plan):

1. Create a project and register a **Web app**. Paste its config object into `FIREBASE_CONFIG` in `index.html`. Those values aren't secret.
2. **Authentication → Sign-in method**: enable **Anonymous** and **Google**.
3. **Authentication → Settings → Authorized domains**: add `lexenson.github.io`.
4. **Firestore Database**: create it in production mode, then publish these rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{db}/documents {
    match /users/{uid}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```

While `FIREBASE_CONFIG` is `null`, there's no sign-in button and nothing leaves the browser.

You can also move stats by file: **Export stats** at the bottom of the page, then **Import stats** on the other device. Importing merges with what's already there and never creates duplicates.

## Hosting

Served by GitHub Pages from the `main` branch (root folder). Every push to `main` redeploys automatically within a minute or two.

To run locally, open `index.html` in a browser, or run `python3 -m http.server` in this folder and visit http://localhost:8000.
