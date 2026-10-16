# The Doc List

A single-page, searchable list of documentaries: the ones I've watched, with my rating next to the Letterboxd average, plus documentaries I haven't seen yet. The list has 259 films: 145 from my 2026 documentary project (marked **Doc project**) and 114 more from my Letterboxd "Documentaries" list. Tap or click a title for a description, my review excerpt, and a link to my review on Letterboxd.

**Live site:** _add your GitHub Pages address here_ (for example `https://<username>.github.io/<repo>/`)

## What it does

- **Search** by title, subject, or where to watch.
- **Filter** by status (All / Watched / Not watched), by list (Everything / Doc project / Other documentaries), subject, my rating, Letterboxd rating, and a range of years.
- **Sort** by my list order, my rating, Letterboxd rating, year (newest or oldest), or title.
- **Detail view** for each film: year, status, subject, where to watch, a short description, an excerpt of my review (watched films), and a link out to Letterboxd.
- Shows both **my rating** and the **Letterboxd community average**, as a number and as stars.
- Works on phones and desktops, with light and dark themes that follow the device setting.

## Reading the list

- An asterisk after a service, such as `Prime*`, means it is **not free to watch** there.
- `AfAm` is short for African-American.
- A **Doc project** badge marks films that were part of my documentary project list. Films without it came from my Letterboxd "Documentaries" list.
- Films marked "Not watched" show only the Letterboxd average, since I haven't rated them.
- A film that isn't on Letterboxd shows "Not on Letterboxd" instead of a link.
- If a watched film has no review link yet, the detail view offers a Letterboxd search instead.

## How it's built

Everything is in one file, `index.html`: markup, styles, script, and the film data. There is no build step and no framework, and no server. The only outside request is the Google Fonts stylesheet (Archivo, Public Sans, IBM Plex Mono). If that fails to load, the page falls back to system fonts.

## Adding or editing films from the page

- The **+** button adds a film. Tap any film, then **Edit** or **Delete** (Delete asks you to tap twice).
- **Backup & restore** (bottom of the page) exports the list as JSON, imports one, or resets to the list published in `index.html`.
- Edits are stored in the browser on that device only. They don't sync between devices and are erased if site data is cleared, so export a backup now and then.
- Until you make your first edit in a browser, it shows whatever is published in `index.html`. After that, the browser's own copy wins, so later changes to `index.html` won't appear there until you use **Reset to published list**.
- New films get a date added; **Date added, newest first** is in the sort menu.

## Adding or editing films in the file

The film data is a JavaScript array named `FILMS` near the bottom of `index.html`. Each film is one line, in list order:

```js
{t:"Writing With Fire", y:2021, lb:3.7, mine:3.5, s:["Media", "Culture"], w:"Prime", seen:1,
 review:"https://boxd.it/…", ex:"Excerpt of my review…", desc:"Short description."},
```

| Field | Meaning |
|---|---|
| `t` | Title |
| `y` | Year (use the Letterboxd year) |
| `lb` | Letterboxd average, or `null` if there isn't one |
| `mine` | My rating. Watched films only; leave it out for unwatched |
| `s` | Subjects, as a list of tags |
| `w` | Where to watch. Add `*` if it isn't free. `""`, `N/A` and `???` are hidden |
| `seen` | `1` if watched; leave it out if not |
| `review` | Link to my Letterboxd review (optional) |
| `ex` | Excerpt of my review (optional) |
| `desc` | Short description (optional; the page shows "Description coming soon." without one) |
| `doc` | `1` if the film is part of the Doc project list (optional) |
| `nolb` | `1` if the film is not on Letterboxd (optional) |

To add a film, copy a line, change the values, and keep the commas and quotes intact. Put a backslash before any double quote inside text (`\"`). After editing, open the page and check that the film appears and that the filters still work.

## Updating the live site

1. Replace `index.html` in the repository (**Add file → Upload files**, then commit).
2. GitHub Pages republishes within a minute or two. If you still see the old version, do a hard refresh.

To host it for the first time: create a public repository, upload `index.html`, then go to **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.

## Where the data came from

- Titles, years, subjects, availability and my ratings come from my own spreadsheet (Doc26).
- My ratings and review excerpts come from my Letterboxd export. Review links are Letterboxd's short `boxd.it` links.
- The 114 added films come from my Letterboxd "Documentaries" list export. Their ratings and review links come from the same export; many watched films there have no rating, so "Mine" shows a dash.
- Letterboxd averages were copied in by hand and will drift over time. **The 114 added films have no average yet** (shown as a dash), except F for Fake.
- Subject tags for the added films are my own judgment from their descriptions, and where to watch is blank for them.
- Descriptions are short summaries written with AI assistance from publicly available film pages, festival and distributor listings, and reviews. They are not copied from Letterboxd. Some may contain mistakes, so please tell me if you spot one.

## Notes

- This is a personal project and is not affiliated with Letterboxd.
- Letterboxd averages and availability change. The list reflects what I knew when I last updated it.
