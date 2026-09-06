# AS Latin Vocabulary

A single-file vocabulary trainer for the OCR AS-level Latin vocabulary list, split into the 24 tests
used with Lower Sixth Latin at Eastbourne College. 848 words.

## Putting it online

1. Create a repository on GitHub.
2. Upload `index.html` and `robots.txt`.
3. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
4. The app appears at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

There is no build step, no server and no dependencies. The whole thing is one HTML file, so it also
works from a memory stick, a shared drive or a VLE upload.

## Keeping it out of search results

`index.html` carries `noindex, nofollow, noarchive, nosnippet` meta tags for the main crawlers. That
is the part that reliably works on GitHub Pages, because it travels with the page itself. Do not
delete those lines from the head.

Two things the meta tag does not cover:

- **`robots.txt` only counts at the root of a domain.** On a project site
  (`username.github.io/repo-name/`) the root is `username.github.io/`, which this repository does not
  control, so a `robots.txt` here is ignored. It is included anyway because it does work if you
  publish this as your user site (`username.github.io`) or on a custom domain.
- **The repository page is indexed separately from the site.** A public repo at
  `github.com/username/repo-name` can be found and links out to the deployed URL. Making the
  repository private stops that, and on a paid GitHub plan the Pages site can still be published
  from a private repo. On the free plan, Pages from a private repo is not published, so the
  alternatives are to keep the repo public but give it an unrevealing name, or to host the file
  somewhere else.

Neither of these is access control. Anyone with the URL can open the page, and the vocabulary list is
readable in the source. If it needs to be genuinely restricted rather than merely unlisted, put it
behind the VLE login instead.

## The six activities

1. **Flashcards** — Latin one side, meanings and parts the other; self-rated, with misses recycled.
2. **Basic test** — every meaning of the word, in any order.
3. **Advanced test** — meanings plus principal parts, genitive and gender.
4. **Forms** — translate a real form (`tulit` → "he carried"), parse it, or give the case and number
   of a noun form. Every valid analysis of an ambiguous form is accepted.
5. **English into Latin** — verb forms, agreeing adjective-noun phrases, prepositional phrases and
   short sentences. Word order is free.
6. **Consolidation** — all of the above mixed, weighted towards words previously got wrong.

Interleaving from earlier tests is a setting available in every activity, not a separate mode.

## Forms are generated, not stored

Modes 4 and 5 build forms at run time from the principal parts and genitives in the list itself:
five noun declensions, three adjective types with comparison, four conjugations plus 3rd -io,
deponents, semi-deponents, impersonals, and the irregulars (`sum`, `possum`, `eo`, `fero`, `volo`,
`nolo`, `malo`, `fio`) with their compounds. Defectives (`odi`, `coepi`, `inquam`, `novi`) and
indeclinables are excluded from form work.

Because 321 senses in the list are shared by more than one word, English-into-Latin questions accept
any word carrying the same sense, inflected to the same slot: "the master" takes `dominus` or
`magister`, "they will demand" takes `postulabunt` or `poscent`.

Two safety valves sit under every answer:

- **"This form looks wrong"** on any generated form. Flags collect under Teacher → Flagged forms.
- **"My answer could be right too"** whenever a typed answer is marked wrong. The mark is given back
  at once and the query lands under Teacher → Queried answers with what the pupil put and what was
  expected. The score code reports how many marks were self-claimed, so nothing is given back
  invisibly.

## Teacher panel

- Decode a pupil's score code (a checksum catches edited codes, and it shows any self-claimed marks).
- Review queried answers and flagged forms.
- Browse the full word list test by test.
- Clear everything stored on the device.

## Printable tests

Print a test in any of three directions, with interleaving and an optional answer key. Prints in two
columns with a name, set, date and total line.

## Data

Progress and flags live in the browser's local storage on each device. Nothing is uploaded and there
are no accounts. Editing the word list means editing the `VOCAB` array near the top of the file.
