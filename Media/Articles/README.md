# Featured Articles — how to add one

Every article lives in its own folder inside `Media/Articles/`. The text and the pictures
for an article stay together in that one folder, so nothing else on the site has to change.

```
Media/Articles/
  index.js                       <- the list of articles, in the order they appear
  _template/                     <- copy this folder to start a new article
    article.js
  the-foundation-of-bhakti/
    article.js                   <- the text
    cover.jpg                    <- picture on the card and at the top of the pop-up
    1.jpg                        <- extra pictures shown at the bottom of the pop-up
    2.jpg
```

## Adding a new article

1. **Copy the `_template` folder** and rename it. Use lowercase words joined by
   hyphens, e.g. `the-power-of-simran`. This name is the folder name only — it is never
   shown to visitors.
2. **Put the pictures inside that new folder.** Any filename works, as long as it matches
   what you write in `article.js`.
3. **Open `article.js` in the new folder** (Notepad or any text editor) and fill it in.
   Only edit the part between `RSSD_ARTICLE(` and `);` — leave those two ends alone.

   | Field      | What it is |
   |------------|------------|
   | `category` | Small orange label above the title, e.g. `Devotion`, `Discourses` |
   | `title`    | Heading of the article |
   | `author`   | Usually `RSSD` |
   | `date`     | Shown as written, e.g. `May 8, 2026` |
   | `cover`    | Filename of the main picture in this folder |
   | `coverAlt` | Short description of the cover picture (read aloud by screen readers) |
   | `excerpt`  | 1–2 line teaser on the card. Leave it as `""` to use the first paragraph automatically |
   | `body`     | The article text — **one line per paragraph**, each in quotes, separated by commas |
   | `images`   | Extra pictures for the pop-up. Leave it as `[]` if there are none |

4. **Add the folder name to `index.js`**, at the top of the list so the newest article
   appears first:

   ```js
   RSSD_ARTICLE_LIST([
     "the-power-of-simran",
     "the-foundation-of-bhakti",
     "all-is-god-nothing-exists-apart-from-him"
   ]);
   ```

That's it — the article appears in the Featured Articles slider on the home page.
Refresh the page to see it (press Ctrl+F5 if the old version is still showing).

## Things to watch out for

- Keep the punctuation exact: every text value in `"double quotes"`, a comma between
  items, and **no comma after the last one**. If an article does not show up, this is
  almost always the reason.
- If the text itself contains a double quote, either use the curly quotes `“ ”`
  (recommended — they look better on the page) or write a straight one as `\"`.
- Save the file as **UTF-8** so that quotes, dashes and Hindi text stay intact.
  Notepad does this by default; in Notepad++ use *Encoding → UTF-8*.
- Keep pictures reasonably sized (roughly 1200–1600 px wide is plenty) so the page
  stays fast on phones.
- The folder is only read when it is listed in `index.js`. `_template` is not listed,
  so it never appears on the site.

## If an article does not appear

Open the page in Chrome, press **F12**, and look at the **Console** tab. A message
starting with `Featured articles:` will name the folder that failed. A red
`SyntaxError` means a missing quote, bracket or comma in that folder's `article.js`.

The rest of the articles keep working even when one file has a mistake, so a typo will
never take the whole section down.
